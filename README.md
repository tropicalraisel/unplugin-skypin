# unplugin-skypin

[![NPM version](https://img.shields.io/npm/v/unplugin-skypin?color=a1b858&label=)](https://www.npmjs.com/package/unplugin-skypin)

Inspired by [rollup-plugin-skypin](https://github.com/MarshallCB/rollup-plugin-skypin#usage),
this plugin provides the same functionality across all the platforms supported by Unplugin!

## Options

Uses parameters similar to RPS:

- `packages` *(Type: String[], Default: `[]`)*: Declare the package imports that should be changed here. Unplugin performs some low-level operations that can involve accessing dependencies that were never intended to be.
- `minified` *(Type: Boolean, Default: `true`)*: Whether to use minified assets.
- `pinned` *(Type: Boolean, Default: `true`)*: Whether to use Skypack's [pinned](https://docs.skypack.dev/skypack-cdn/api-reference/pinned-urls-optimized#generate-a-pinned-url) assets (recommended, even in development).
- `replace` *(Type: function(id: string) => boolean|string, Default: `() => true`)*: Uses a returned string as the package **id**. Returning a boolean value simply toggles Skypack URL substitution.

[Package import formats supported by Skypin](https://github.com/marshallcb/skypin#skypinmodule_id-options---url) should be used
as the package import and when declaring a package in `packages`.

## Usage

```bash
pnpm i
```

Check the `package.json` for the available scripts.

## Install

```bash
npm i unplugin-skypin
```

<details>
<summary>Vite</summary><br>

```ts
// vite.config.{m}js
import skypin from 'unplugin-skypin/vite'
import { defineConfig } from 'vite'

export default defineConfig({
  plugins: [
    skypin({
      packages: [
        /* imports to change here */
      ],
      /* other options */
    }),
  ],
})
```

<br></details>

<details>
<summary>Rollup</summary><br>

```ts
// rollup.config.{m}js
import skypin from 'unplugin-skypin/rollup'

export default {
  input: 'src/index.js',
  output: {
    dir: 'dist',
    format: 'esm',
  },
  plugins: [
    skypin({
      packages: [
        /* imports to change here */
      ],
      /* other options */
    }),
  ],
}
```

<br></details>


<details>
<summary>Webpack</summary><br>

```ts
// webpack.config.{c}js
module.exports = {
  /* ... */
  plugins: [
    require('unplugin-skypin/webpack')({ /* options */ })
  ]
}
```

<br></details>

<details>
<summary>Nuxt</summary><br>

```ts
// nuxt.config.{m}js
export default {
  buildModules: [
    ['unplugin-skypin/nuxt', { /* options */ }],
  ],
}
```

> This module works for both Nuxt 2 and [Nuxt Vite](https://github.com/nuxt/vite)

<br></details>

<details>
<summary>Vue CLI</summary><br>

```ts
// vue.config.{c}js
module.exports = {
  configureWebpack: {
    plugins: [
      require('unplugin-skypin/webpack')({ /* options */ }),
    ],
  },
}
```

<br></details>
