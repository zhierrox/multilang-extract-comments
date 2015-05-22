# multilang-extract-comments [![NPM version](https://badge.fury.io/js/multilang-extract-comments.svg)](http://badge.fury.io/js/multilang-extract-comments)  [![Build Status](https://travis-ci.org/nknapp/multilang-extract-comments.svg)](https://travis-ci.org/nknapp/multilang-extract-comments)  [![Coverage Status](https://img.shields.io/coveralls/nknapp/multilang-extract-comments.svg)](https://coveralls.io/r/nknapp/multilang-extract-comments)

> Extract comments from source files of various languages

## Overview

multilang-extract-comments is a package for extracting comments from source-code. It is compatible with the 
`extract-comments`-package by Jon Schlinkert:

It provides an extended API, which allows you to extract comments not only from JavaScript
files, but also from Python, C, Handlebars etc.

The module is inspired by `extract-comment`. It's purpose is to allow `verb` to extract of
jsdoc-like comments from other files as well. The primary targets are Handlebars-files, for 
documenting [bootprint template-modules](https://github.com/nknapp/bootprint).

## Example (JavaScript)

For the following string:

```js
/**
 * A javascript multiline-comment
 * with multiple lines
 */
function aLineOfCode() {

}

// A single line comments
// More of it directly below
function anotherFunction() {
  aLineOfCode();
}

anotherFunction();

```

and the following code

```js
var comments = require('multilang-extract-comments')(string);
``

The variable `comments` now contains:

```json
{
  "1": {
    "begin": 1,
    "end": 4,
    "codeStart": 5,
    "content": "A javascript multiline-comment\nwith multiple lines\n",
    "code": "function aLineOfCode() {"
  },
  "9": {
    "begin": 9,
    "end": 11,
    "codeStart": 11,
    "content": "A single line comments\nMore of it directly below\n",
    "code": "function anotherFunction() {"
  }
}
```

Also have a look at the usage example of `extract-comments`

## Example (Handlebars)

For the following string:

```hbs
{{!
   This is an example
   of a handlebars multiline-comment.
}}
Some code here
```

and the following code

```hbs
var comments = require('multilang-extract-comments')(string, { filename: 'handlebars.hbs'});
``

The variable `comments` now contains:

```json
{
  "1": {
    "begin": 1,
    "end": 4,
    "codeStart": 5,
    "content": "This is an example\nof a handlebars multiline-comment.\n",
    "code": "Some code here"
  }
}
```

### API

## Running tests

Install dev dependencies:

```sh
$ npm i -d && npm test
```

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/nknapp/multilang-extract-comments/issues/new)

see [CONTRIBUTING.md](./CONTRIBUTING.md)

## Author

**Nils Knappmeier**

+ [github/nknapp](https://github.com/nknapp)
+ [twitter/knappi79](http://twitter.com/knappi79)

## Related 

* [comment-patterns](https://github.com/nknapp/language-comments): A list of comment-patterns for different languages
* [extract-comments](https://github.com/jonschlinkert/extract-comments): Extract code comments from string or from a glob of files.

## License

Copyright © 2015 Nils Knappmeier
Released under the MIT license.

# Change Log

This project adheres to [Semantic Versioning](http://semver.org/).

## Upcoming

### Initial version

<!-- reflinks generated by verb-reflinks plugin -->

[assemble]: http://assemble.io
[template]: https://github.com/jonschlinkert/template
[verb]: https://github.com/assemble/verb