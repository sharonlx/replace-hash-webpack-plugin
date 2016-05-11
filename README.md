# Replace Hash Webpack plugin

[![npm version](https://badge.fury.io/js/replace-hash-webpack-plugin.svg)](http://badge.fury.io/js/replace-hash-webpack-plugin)

This is a [webpack](http://webpack.github.io/) plugin that update script references in HTML files by webpack bundle's hash.

## Installation

Install the plugin with npm:
```shell
$ npm install replace-hash-webpack-plugin --save-dev
```

## Configuration

You can pass a hash of configuration options to `ReplaceHashWebpackPlugin`.
Allowed values are as follows:

- `src`: Original file.
- `dest`: New file with replaced data.

## Example

```javascript
//webpack.config.js
var ReplaceHashWebpackPlugin = require('replace-hash-webpack-plugin');
var webpackConfig = {
  entry: 'main.js',
  output: {
    filename: '[name].[hash].js',
    publicPath: '/js/',
  },
  plugins: [
    new ReplaceHashWebpackPlugin({
      src: 'index.html',
      dest: 'build/index.html',
    })
  ]
};
```

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>replace-hash-webpack-plugin</title>
</head>
<body>
  <script src="/js/main.js"></script>
</body>
</html>
```

#### result:

```html
<!-- build/index.html -->
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>replace-hash-webpack-plugin</title>
</head>
<body>
  <script src="main.e8f4f5aa3f6ce31e1537.js"></script>
</body>
</html>
```
