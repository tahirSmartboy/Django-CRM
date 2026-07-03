FROM node:22-slim

# Pin pnpm to a known-good, tested version instead of "latest"
RUN corepack enable && corepack prepare pnpm@11.9.0 --activate

WORKDIR /app

ENV CI=true

# Install dependencies (layer cached) — pnpm-workspace.yaml must be present for allowBuilds to load
COPY package.json pnpm-lock.yaml* pnpm-workspace.yaml ./
RUN pnpm install --frozen-lockfile

EXPOSE 5173

CMD ["pnpm", "dev", "--host", "0.0.0.0"]