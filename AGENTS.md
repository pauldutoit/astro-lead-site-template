## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Working from a `.claude/worktrees/*` worktree

If you are in an isolated worktree (path contains `.claude/worktrees/`), Vite's
tsconfig resolver walks up the tree and finds the parent checkout's
`tsconfig.json`. That file also `extends "astro/tsconfigs/strict"`, so if the
parent checkout has no `node_modules` the extends fails with
`Tsconfig not found astro/tsconfigs/strict` during `astro sync` or `astro build`.

Fix: make sure the parent checkout (the real repo root, not the worktree) has a
`node_modules`. Cheapest option — symlink from the parent to the worktree's
copy, since they share the same lockfile:

```
ln -s <worktree>/node_modules <parent-checkout>/node_modules
```

Or run `npm install` at both levels. Do this once per site.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)
