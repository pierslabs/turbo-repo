# Turborepo starter

1. Install

```
 npm install turbo --global
```

2. Create new Repo

```
npx create-turbo@latest

turbo dev   <==== | Run cmd example|
```

3. Add new App or Package

```
turbo gen workspace --name fake-package
```

4. Global package

- In fake-package find package.json in name prop rename to convention

```
{
 "name": "@repo/fake-package",
 "version": "0.0.0",
 "private": true,
  "exports": {
   "./sum": "./src/sum.ts" // add files to export
 },
 ....
 }
```

5. Copy and name and add it to the app or package that needs it in the dependencies

```
 "dependencies": {
   "@repo/ui": "*",
   "next": "^15.1.6",
   "react": "^19.0.0",
   "react-dom": "^19.0.0",
   "@repo/fake-package": "*"   <==== | Add new package|
 },
 ....
```

6. Add cmd 'example tests'
7. In root dir find turbo.json add in tasks

```
   "dev": {
    "cache": false,
    "persistent": true
  },
  "test": {
    "cache": true,
    "dependsOn": ["^test"]
  }
```

8. In root dir find package.json add in scripts cmd

```
  "scripts": {
  "build": "turbo build",
  "dev": "turbo dev",
  "lint": "turbo lint",
  "format": "prettier --write \"**/*.{ts,tsx,md}\"",
  "test": "turbo test"  <==== | Add new cmd|
},
```

This Turborepo starter is maintained by the Turborepo core team.

## Using this example

Run the following command:

```sh
npx create-turbo@latest
```

## What's inside?

This Turborepo includes the following packages/apps:

### Apps and Packages

- `docs`: a [Next.js](https://nextjs.org/) app
- `web`: another [Next.js](https://nextjs.org/) app
- `@repo/ui`: a stub React component library shared by both `web` and `docs` applications
- `@repo/eslint-config`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `@repo/typescript-config`: `tsconfig.json`s used throughout the monorepo

Each package/app is 100% [TypeScript](https://www.typescriptlang.org/).

### Utilities

This Turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting

### Build

To build all apps and packages, run the following command:

```
cd my-turborepo
pnpm build
```

### Develop

To develop all apps and packages, run the following command:

```
cd my-turborepo
pnpm dev
```

### Remote Caching

> [!TIP]
> Vercel Remote Cache is free for all plans. Get started today at [vercel.com](https://vercel.com/signup?/signup?utm_source=remote-cache-sdk&utm_campaign=free_remote_cache).

Turborepo can use a technique known as [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup?utm_source=turborepo-examples), then enter the following commands:

```
cd my-turborepo
npx turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

```
npx turbo link
```

## Useful Links

Learn more about the power of Turborepo:

- [Tasks](https://turbo.build/repo/docs/core-concepts/monorepos/running-tasks)
- [Caching](https://turbo.build/repo/docs/core-concepts/caching)
- [Remote Caching](https://turbo.build/repo/docs/core-concepts/remote-caching)
- [Filtering](https://turbo.build/repo/docs/core-concepts/monorepos/filtering)
- [Configuration Options](https://turbo.build/repo/docs/reference/configuration)
- [CLI Usage](https://turbo.build/repo/docs/reference/command-line-reference)
