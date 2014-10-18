# [gulp](https://github.com/wearefractal/gulp)-template-compile

Compile [Lo-Dash templates](http://lodash.com/docs#template) (should work with [Underscore templates](http://underscorejs.org/#template) too).

Forked from [https://github.com/ingro/gulp-template-compile]. Same in every way except for the namespace option which now allows dot-notated Strings.

## Synopsis

This plugin is heavily inspired by [Sindre Sorhus](https://github.com/sindresorhus)'s [gulp-nunjucks](https://github.com/sindresorhus/gulp-nunjucks) plugin, in fact I used it as skeleton for creating this one.

## Install

Install with [npm](https://www.npmjs.org/package/gulp-template-compile)

```
npm install --save-dev gulp-template-compile
```

## Example

### `gulpfile.js`

```js
var gulp = require('gulp');
var template = require('gulp-template-compile');
var concat = require('gulp-concat');

gulp.task('default', function () {
	gulp.src('src/*.html')
		.pipe(template())
		.pipe(concat('templates.js'))
		.pipe(gulp.dest('dist'));
});
```

## API

See the [Lo-Dash `_.template` docs](http://lodash.com/docs#template).


### template(options)

### options

Type: `Object`

#### options.name

Type: `Function`
Default: *Relative template path. Example: `templates/list.html`*

You can override the default behavior by supplying a function which gets the current [File](https://github.com/wearefractal/vinyl#constructoroptions) object and is expected to return the name.

Example:

```js
{
	name: function (file) {
		return 'tpl-' + file.relative;
	}
}
```

#### options.namespace
Type: `String`
Default: 'window.JST'

The namespace in which the precompiled templates will be assigned e.g. `window.myNamespace.templates`.

If not provided, the `window.JST` namespace will be created if it does not already exist.

If provided, the namespace must already exist otherwise an error will result.


#### options.templateSettings
Type: `Object`
Default: null

[Lo-Dash `_.template` options](http://lodash.com/docs#template).


## Notes

If you use [grunt](http://gruntjs.com) instead of gulp, but want to perform a similar task, use [grunt-contrib-jst](https://github.com/gruntjs/grunt-contrib-jst).


## License

MIT © Emanuele Ingrosso