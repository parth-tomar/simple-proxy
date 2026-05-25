# Contributing to simple-proxy

Thanks for your interest in contributing! This document covers everything you need to get started.

---

## Prerequisites

- **Node.js** v18 or later
- **pnpm** — this repo enforces pnpm via `preinstall`. Install it with:
  ```bash
  npm install -g pnpm
  ```

---

## Local setup

```bash
# 1. Fork the repo, then clone your fork
git clone https://github.com/<your-username>/simple-proxy.git
cd simple-proxy

# 2. Install dependencies
pnpm install

# 3. Start the dev server (Node.js preset by default)
pnpm dev
```

The proxy will be running at `http://localhost:3000`.

---

## Branch structure

> **`dev` is the default and active branch** — not `main`.

Always branch off `dev` and open your pull request against `dev`.

```bash
git checkout dev
git pull origin dev
git checkout -b your-feature-branch
```

---

## Making changes

### Linting

The project uses ESLint with the Airbnb base config and Prettier. Before pushing:

```bash
# Check for lint errors
pnpm lint

# Auto-fix what's fixable
pnpm lint:fix
```

TypeScript type errors will also surface during `pnpm build` — make sure that passes too.

### Building for a specific platform

Use the platform-specific build scripts to verify your changes work across targets:

| Platform            | Command                  |
| ------------------- | ------------------------ |
| Cloudflare Workers  | `pnpm build:cloudflare`  |
| AWS Lambda          | `pnpm build:aws`         |
| Node.js             | `pnpm build:node`        |
| Netlify Edge        | `pnpm build:netlify`     |

If your change touches platform-specific behaviour, test the relevant build locally before opening a PR.

---

## Submitting a pull request

1. Make sure `pnpm lint` passes with no errors.
2. Keep commits focused — one logical change per commit.
3. Write a clear PR description: **what** changed and **why**.
4. Open the PR against the `dev` branch.
5. Link any related issues in the description (e.g. `Closes #12`).

---

## Project structure

```
src/           # All source TypeScript lives here
.github/       # CI workflows
nitro.config.ts  # Nitro framework config
wrangler.toml    # Cloudflare Workers config
netlify.toml     # Netlify config
Dockerfile       # Docker / self-hosted Node.js
```

---

## Need help?

Check the proxy docs at https://docs.pstream.org/proxy/introduction or open an issue describing what you're trying to do.
