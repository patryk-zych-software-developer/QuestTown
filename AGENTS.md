# QuestTown

Next.js 16 App Router, React 19, TypeScript (strict), Tailwind CSS 4, Bun.

## Commands

```bash
bun install
bun run dev
bun run build
bun run lint
bun run format
bun run format:check
bun run typecheck
```

Use **Bun**, not npm/yarn/pnpm. CI runs `lint`, `format:check`, and `typecheck`.

## Layout

- `src/app/` — App Router routes, layouts, pages
- Path alias: `@/*` → `./src/*`
- Config: `eslint.config.mjs`, `.prettierrc`, `tsconfig.json`

## Code style

- Functional components and hooks only. Never class components.
- Prefer named exports for shared modules; Next.js `page.tsx` / `layout.tsx` keep default exports.
- TypeScript strict. Avoid `any` unless unavoidable and briefly justified.
- Tailwind utility classes in JSX; keep global CSS minimal (`globals.css`).

```tsx
// CORRECT
export function QuestTitle({ label }: { label: string }) {
  return <h1 className="text-2xl font-semibold">{label}</h1>;
}

// WRONG — class component
export class QuestTitle extends React.Component<{ label: string }> {
  render() {
    return <h1>{this.props.label}</h1>;
  }
}
```

## Boundaries

- Never commit `.env*` or secrets.
- Do not edit generated output under `.next/`.
- Do not invent package managers or CI tools outside Bun + GitHub Actions.

## Git / PRs

- Conventional commits: `feat:`, `fix:`, `ci:`, `docs:`, `chore:`.
- Before finishing: `bun run lint`, `bun run format:check`, `bun run typecheck`.
- When the work closes a GitHub Issue, the PR body **must** include a closing keyword, e.g. `Closes #12` or `Fixes #12` (enables Project Status automation).
