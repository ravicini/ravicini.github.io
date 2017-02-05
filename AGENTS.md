# Agent Instructions

This is a personal blog/documentation website built with Docusaurus 3.9.2, deployed to GitHub Pages at https://ravicini.ch.

## Build, Test, and Development Commands

```bash
# Install dependencies (use npm or yarn)
pnpm install

# Start local development server (with hot reload)
pnpm start          # Runs on http://localhost:3000

# Build for production
pnpm run build      # Outputs to build/ directory

# Type check TypeScript
pnpm run typecheck

# Preview production build locally
pnpm run serve

# Deploy to GitHub Pages
pnpm run deploy                              # Without SSH
GIT_USER=<username> pnpm run deploy         # Specify GitHub user
USE_SSH=true pnpm run deploy                # With SSH

# Clear Docusaurus cache and generated files
pnpm run clear
```

## Project Structure

- **`blog/`** - Blog posts in Markdown/MDX format
  - Posts can be single files (e.g., `2019-05-28-first-blog-post.md`)
  - Or folders with `index.md` + assets (e.g., `2021-08-26-welcome/`)
  - `authors.yml` - Blog author definitions
  - `tags.yml` - Tag definitions
  
- **`docs/`** - Documentation pages in Markdown/MDX
  - Tutorial sidebar is auto-generated from directory structure (see `sidebars.ts`)
  
- **`src/`** - Custom React components and pages
  - `src/pages/` - Custom standalone pages (e.g., homepage at `index.tsx`)
  - `src/components/` - React components used across the site
  - `src/css/custom.css` - Global custom styles
  
- **`static/`** - Static assets (images, favicon, etc.) served at site root

- **Configuration files:**
  - `docusaurus.config.ts` - Main Docusaurus configuration (site metadata, theme, navbar, footer, plugins)
  - `sidebars.ts` - Documentation sidebar configuration
  - `tsconfig.json` - TypeScript configuration

## Key Conventions

### Docusaurus-Specific Patterns

- **Module aliases:** Use `@site/` to reference the project root (e.g., `@site/src/components/Foo`, `@site/static/img/logo.svg`)
- **Theme components:** Use `@theme/` to import Docusaurus theme components (e.g., `@theme/Layout`, `@theme/Heading`)
- **Docusaurus hooks:** Import from `@docusaurus/` packages (e.g., `useDocusaurusContext`, `Link`)

### Configuration

- **Future flags enabled:** `future.v4: true` is set for better v4 compatibility
- **Deployment:** GitHub Pages deployment configured for `ravicini/ravicini.github.io` with `gh-pages` branch
- **i18n:** Currently English-only (`defaultLocale: 'en'`)
- **onBrokenLinks:** Set to `'throw'` - broken links will fail the build
- **Color mode:** Respects system preference (`respectPrefersColorScheme: true`)

### Content Authoring

- Use Markdown (`.md`) or MDX (`.mdx`) for blog posts and docs
- Blog posts support frontmatter metadata, reading time, RSS/Atom feeds
- Blog enforces best practices (warnings for inline tags, inline authors, untruncated posts)

### React Components

- All components use TypeScript (`.tsx`)
- Return type should be `ReactNode` for component functions
- Use `clsx` for conditional className combinations
- SVG imports: Use `require('@site/static/img/foo.svg').default` pattern
