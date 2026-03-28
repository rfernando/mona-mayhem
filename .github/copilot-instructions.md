# Mona Mayhem

A retro arcade-themed GitHub Contribution Battle Arena built with Astro v5. Users enter two GitHub usernames and see their contribution graphs compared in a game-show battle format.

## Build & Dev Commands

```bash
npm run dev        # Start dev server (http://localhost:4321)
npm run build      # Build for production
npm run preview    # Preview production build locally
```

## Architecture

- `src/pages/` — Astro pages (`.astro` files)
- `src/pages/api/` — Server-side API routes (`.ts` files using Astro's `APIRoute`)
- `public/` — Static assets served as-is
- `astro.config.mjs` — SSR config with `@astrojs/node` adapter (standalone mode)

The app uses **server-side rendering** (`output: 'server'`). All pages and API routes run on the server by default. Use `export const prerender = true` only for pages that can be statically generated.

## Astro Conventions

- **API routes** live under `src/pages/api/` and export named handlers (`GET`, `POST`, etc.) typed as `APIRoute`
- **Dynamic routes** use bracket syntax: `[username].ts`, `[...slug].astro`
- Always set `export const prerender = false` on API routes to ensure they are server-rendered
- Access route params via `({ params, request })` in API handlers
- Prefer inline `<style>` in `.astro` files (scoped by default); use `is:global` sparingly
- Component frontmatter (between `---`) is server-only — safe for secrets and Node APIs
- TypeScript is strict (`astro/tsconfigs/strict`); avoid `any`, use Astro's generated types in `.astro/types.d.ts`

## Project Style

- Retro arcade aesthetic — "Press Start 2P" Google Font, pixel art, neon colors
- No UI framework (no React/Vue); use Astro components and vanilla JS for interactivity
