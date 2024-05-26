# @zitterorg/reiciendis-culpa

[![npm version](https://img.shields.io/npm/v/@zitterorg/reiciendis-culpa.svg)](https://www.npmjs.com/package/@zitterorg/reiciendis-culpa)
[![Downloads/month](https://img.shields.io/npm/dm/@zitterorg/reiciendis-culpa.svg)](http://www.npmtrends.com/@zitterorg/reiciendis-culpa)
[![Build Status](https://github.com/zitterorg/reiciendis-culpa/workflows/CI/badge.svg)](https://github.com/zitterorg/reiciendis-culpa/actions)
[![codecov](https://codecov.io/gh/zitterorg/reiciendis-culpa/branch/main/graph/badge.svg)](https://codecov.io/gh/zitterorg/reiciendis-culpa)

A regular expression parser for ECMAScript.

## 💿 Installation

```bash
$ npm install @zitterorg/reiciendis-culpa
```

- require Node@^12.0.0 || ^14.0.0 || >=16.0.0.

## 📖 Usage

```ts
import {
    AST,
    RegExpParser,
    RegExpValidator,
    RegExpVisitor,
    parseRegExpLiteral,
    validateRegExpLiteral,
    visitRegExpAST
} from "@zitterorg/reiciendis-culpa"
```

### parseRegExpLiteral(source, options?)

Parse a given regular expression literal then make AST object.

This is equivalent to `new RegExpParser(options).parseLiteral(source)`.

- **Parameters:**
    - `source` (`string | RegExp`) The source code to parse.
    - `options?` ([`RegExpParser.Options`]) The options to parse.
- **Return:**
    - The AST of the regular expression.

### validateRegExpLiteral(source, options?)

Validate a given regular expression literal.

This is equivalent to `new RegExpValidator(options).validateLiteral(source)`.

- **Parameters:**
    - `source` (`string`) The source code to validate.
    - `options?` ([`RegExpValidator.Options`]) The options to validate.

### visitRegExpAST(ast, handlers)

Visit each node of a given AST.

This is equivalent to `new RegExpVisitor(handlers).visit(ast)`.

- **Parameters:**
    - `ast` ([`AST.Node`]) The AST to visit.
    - `handlers` ([`RegExpVisitor.Handlers`]) The callbacks.

### RegExpParser

#### new RegExpParser(options?)

- **Parameters:**
    - `options?` ([`RegExpParser.Options`]) The options to parse.

#### parser.parseLiteral(source, start?, end?)

Parse a regular expression literal.

- **Parameters:**
    - `source` (`string`) The source code to parse. E.g. `"/abc/g"`.
    - `start?` (`number`) The start index in the source code. Default is `0`.
    - `end?` (`number`) The end index in the source code. Default is `source.length`.
- **Return:**
    - The AST of the regular expression.

#### parser.parsePattern(source, start?, end?, flags?)

Parse a regular expression pattern.

- **Parameters:**
    - `source` (`string`) The source code to parse. E.g. `"abc"`.
    - `start?` (`number`) The start index in the source code. Default is `0`.
    - `end?` (`number`) The end index in the source code. Default is `source.length`.
    - `flags?` (`{ unicode?: boolean, unicodeSets?: boolean }`) The flags to enable Unicode mode, and Unicode Set mode.
- **Return:**
    - The AST of the regular expression pattern.

#### parser.parseFlags(source, start?, end?)

Parse a regular expression flags.

- **Parameters:**
    - `source` (`string`) The source code to parse. E.g. `"gim"`.
    - `start?` (`number`) The start index in the source code. Default is `0`.
    - `end?` (`number`) The end index in the source code. Default is `source.length`.
- **Return:**
    - The AST of the regular expression flags.

### RegExpValidator

#### new RegExpValidator(options)

- **Parameters:**
    - `options` ([`RegExpValidator.Options`]) The options to validate.

#### validator.validateLiteral(source, start, end)

Validate a regular expression literal.

- **Parameters:**
    - `source` (`string`) The source code to validate.
    - `start?` (`number`) The start index in the source code. Default is `0`.
    - `end?` (`number`) The end index in the source code. Default is `source.length`.

#### validator.validatePattern(source, start, end, flags)

Validate a regular expression pattern.

- **Parameters:**
    - `source` (`string`) The source code to validate.
    - `start?` (`number`) The start index in the source code. Default is `0`.
    - `end?` (`number`) The end index in the source code. Default is `source.length`.
    - `flags?` (`{ unicode?: boolean, unicodeSets?: boolean }`) The flags to enable Unicode mode, and Unicode Set mode.

#### validator.validateFlags(source, start, end)

Validate a regular expression flags.

- **Parameters:**
    - `source` (`string`) The source code to validate.
    - `start?` (`number`) The start index in the source code. Default is `0`.
    - `end?` (`number`) The end index in the source code. Default is `source.length`.

### RegExpVisitor

#### new RegExpVisitor(handlers)

- **Parameters:**
    - `handlers` ([`RegExpVisitor.Handlers`]) The callbacks.

#### visitor.visit(ast)

Validate a regular expression literal.

- **Parameters:**
    - `ast` ([`AST.Node`]) The AST to visit.

## 📰 Changelog

- [GitHub Releases](https://github.com/zitterorg/reiciendis-culpa/releases)

## 🍻 Contributing

Welcome contributing!

Please use GitHub's Issues/PRs.

### Development Tools

- `npm test` runs tests and measures coverage.
- `npm run build` compiles TypeScript source code to `index.js`, `index.js.map`, and `index.d.ts`.
- `npm run clean` removes the temporary files which are created by `npm test` and `npm run build`.
- `npm run lint` runs ESLint.
- `npm run update:test` updates test fixtures.
- `npm run update:ids` updates `src/unicode/ids.ts`.
- `npm run watch` runs tests with `--watch` option.

[`AST.Node`]: src/ast.ts#L4
[`RegExpParser.Options`]: src/parser.ts#L743
[`RegExpValidator.Options`]: src/validator.ts#L220
[`RegExpVisitor.Handlers`]: src/visitor.ts#L291
