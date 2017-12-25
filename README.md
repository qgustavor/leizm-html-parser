[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][coveralls-image]][coveralls-url]
[![David deps][david-image]][david-url]
[![node version][node-image]][node-url]
[![npm download][download-image]][download-url]
[![npm license][license-image]][download-url]

[npm-image]: https://img.shields.io/npm/v/@leizm/html-parser.svg?style=flat-square
[npm-url]: https://npmjs.org/package/@leizm/html-parser
[travis-image]: https://img.shields.io/travis/leizongmin/leizm-html-parser.svg?style=flat-square
[travis-url]: https://travis-ci.org/leizongmin/leizm-html-parser
[coveralls-image]: https://img.shields.io/coveralls/leizongmin/leizm-html-parser.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/leizongmin/leizm-html-parser?branch=master
[david-image]: https://img.shields.io/david/leizongmin/leizm-html-parser.svg?style=flat-square
[david-url]: https://david-dm.org/leizongmin/leizm-html-parser
[node-image]: https://img.shields.io/badge/node.js-%3E=_4.0-green.svg?style=flat-square
[node-url]: http://nodejs.org/download/
[download-image]: https://img.shields.io/npm/dm/@leizm/html-parser.svg?style=flat-square
[download-url]: https://npmjs.org/package/@leizm/html-parser
[license-image]: https://img.shields.io/npm/l/@leizm/html-parser.svg

# @leizm/html-parser

Fast HTML parser written in pure JavaScript

## Installation

```bash
npm install @leizm/html-parser --save
```

## Usage

```typescript
import * as html from "@leizm/html-parser";

const { errors, nodes } = html.parse(`<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
  <h1>Hello, world! <small>by @leizm/html-parser</small></h1>
  <p>Fast HTML parser written in pure JavaScript</p>
</body>
</html>`);

console.log(html.toString(nodes));
```

the result of `html.parse()` will be:

```json
{
  "errors": [],
  "nodes": [
    { "tagName": "!DOCTYPE", "properties": { "html": true } },
    "\n",
    {
      "tagName": "html",
      "properties": { "lang": "en" },
      "children": [
        "\n",
        {
          "tagName": "head",
          "children": [
            "\n  ",
            { "tagName": "meta", "properties": { "charset": "UTF-8" } },
            "\n  ",
            {
              "tagName": "meta",
              "properties": {
                "name": "viewport",
                "content": "width=device-width, initial-scale=1.0"
              }
            },
            "\n  ",
            {
              "tagName": "meta",
              "properties": {
                "http-equiv": "X-UA-Compatible",
                "content": "ie=edge"
              }
            },
            "\n  ",
            { "tagName": "title", "children": ["Document"] },
            "\n"
          ]
        },
        "\n",
        {
          "tagName": "body",
          "children": [
            "\n  ",
            {
              "tagName": "h1",
              "children": [
                "Hello, world! ",
                { "tagName": "small", "children": ["by @leizm/html-parser"] }
              ]
            },
            "\n  ",
            {
              "tagName": "p",
              "children": ["Fast HTML parser written in pure JavaScript"]
            },
            "\n"
          ]
        },
        "\n"
      ]
    }
  ]
}
```

the result of `html.toString()` will be:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <title>Document</title>
</head>
<body>
  <h1>Hello, world! <small>by @leizm/html-parser</small></h1>
  <p>Fast HTML parser written in pure JavaScript</p>
</body>
</html>
```

## License

```text
MIT License

Copyright (c) 2017 Zongmin Lei <leizongmin@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
