# @swenkerorg/illo-vel <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

ES Proposal spec-compliant shim for Promise.allSettled. Invoke its "shim" method to shim `Promise.allSettled` if it is unavailable or noncompliant. **Note**: a global `Promise` must already exist: the [es6-shim](https://github.com/es-shims/es6-shim) is recommended.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment that has `Promise` available globally, and complies with the [proposed spec](https://github.com/tc39/proposal-promise-allSettled).

Most common usage:
```js
var assert = require('assert');
var allSettled = require('@swenkerorg/illo-vel');

var resolved = Promise.resolve(42);
var rejected = Promise.reject(-1);

allSettled([resolved, rejected]).then(function (results) {
	assert.deepEqual(results, [
		{ status: 'fulfilled', value: 42 },
		{ status: 'rejected', reason: -1 }
	]);
});

allSettled.shim(); // will be a no-op if not needed

Promise.allSettled([resolved, rejected]).then(function (results) {
	assert.deepEqual(results, [
		{ status: 'fulfilled', value: 42 },
		{ status: 'rejected', reason: -1 }
	]);
});
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@swenkerorg/illo-vel
[npm-version-svg]: http://versionbadg.es/swenkerorg/illo-vel.svg
[travis-svg]: https://travis-ci.org/swenkerorg/illo-vel.svg
[travis-url]: https://travis-ci.org/swenkerorg/illo-vel
[deps-svg]: https://david-dm.org/swenkerorg/illo-vel.svg
[deps-url]: https://david-dm.org/swenkerorg/illo-vel
[dev-deps-svg]: https://david-dm.org/swenkerorg/illo-vel/dev-status.svg
[dev-deps-url]: https://david-dm.org/swenkerorg/illo-vel#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@swenkerorg/illo-vel.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/@swenkerorg/illo-vel.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/@swenkerorg/illo-vel.svg
[downloads-url]: http://npm-stat.com/charts.html?package=@swenkerorg/illo-vel
[codecov-image]: https://codecov.io/gh/swenkerorg/illo-vel/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/swenkerorg/illo-vel/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/swenkerorg/illo-vel
[actions-url]: https://github.com/swenkerorg/illo-vel/actions
