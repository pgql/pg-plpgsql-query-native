# @sqlutils/parse

The real PostgreSQL parser, exposed for nodejs.

This is based on the output of [libpg_query](https://github.com/lfittl/libpg_query). This wraps the static library output and links it into a node module for use in js.

All credit for the hard problems goes to [Lukas Fittl](https://github.com/lfittl).

## Requirements

Install node-gyp globally

```sh
npm install node-gyp -g
```

## Installation

```sh
npm install @sqlutils/parse
```

### Documentation

### `query.parseQuery(sql)`/`parseQuerySync`

Parses the sql and returns a Promise for the parse tree (or returns the parse tree directly in the sync version). May reject with/throw a parse error.

The return value is an array, as multiple queries may be provided in a single string (semicolon-delimited, as Postgres expects).

### `query.parsePlPgSQL(funcsSql)`/`query.parsePlPgSQLSync(funcsSql)`

Parses the contents of a PL/PGSql function, from a `CREATE FUNCTION` declaration, and returns a Promise for the parse tree (or returns the parse tree directly in the sync version). May reject with/throw a parse error.

## Example

```js
const parser = require('@sqlutils/parse');
parser.parseQuery('select 1').then(console.log);
```

## Related

* [libpg_query](https://github.com/lfittl/libpg_query)
* [pg_query](https://github.com/lfittl/pg_query)
* [pg_query.go](https://github.com/lfittl/pg_query.go)
