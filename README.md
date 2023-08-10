# fastify-polyglot-typescript

A plugin to handle i18n using [node-polyglot](https://www.npmjs.com/package/node-polyglot), with TypeScript support.

![Node.js CI](https://github.com/topiocom/fastify-polyglot/workflows/Node.js%20CI/badge.svg)

## Install

```bash
$ npm i --save fastify-polyglot-typescript
```

## Usage

```ts
import * as path from "path";
import * as fastify from "fastify";
import fastifyPolyglot from "fastify-polyglot-typescript";

const app = fastify();

app.register(fastifyPolyglot, {
  defaultLocale: "en",
  localesPath: path.join(__dirname, "./locales"),
});

app.listen(3000, (err) => {
  if (err) {
    console.error(err);
    process.exit(1);
  }
  console.log("Server is running on port 3000");
});
```

## Options

| Name            | Description                                                                 |
| --------------- | --------------------------------------------------------------------------- |
| `defaultLocale` | The default locale code to be used (`en` by default).                       |
| `localesPath`   | The folder from where to load locale dictionaries (`./locales` by default). |

## Types

TypeScript types are included in this package to provide better development experience. You can use these types to define the structure of your locale dictionaries and access the `i18n` instance on your Fastify app.

Example usage of types:

```ts
import fastify, { FastifyInstance } from "fastify";
import fastifyPolyglot, {
  FastifyPolyglotOptions,
  PolyglotInstance,
} from "fastify-polyglot-typescript";

const app: FastifyInstance = fastify();

declare module "fastify" {
  interface FastifyInstance {
    i18n: PolyglotInstance;
  }
}

app.register(fastifyPolyglot, {
  defaultLocale: "en",
  localesPath: path.join(__dirname, "./locales"),
});

app.listen(3000, (err) => {
  if (err) {
    console.error(err);
    process.exit(1);
  }
  console.log("Server is running on port 3000");
});
```

## Test

```bash
$ npm test
```

## Acknowledgements

This project is kindly sponsored by:

[Your Sponsor's Name](https://www.your-sponsor-link.com)

## License

Licensed under [MIT](./LICENSE)
