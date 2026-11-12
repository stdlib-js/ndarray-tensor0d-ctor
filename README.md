<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Tensor0D

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create a zero-dimensional [ndarray][@stdlib/ndarray/ctor].

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/ndarray-tensor0d-ctor
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var tensor0d = require( '@stdlib/ndarray-tensor0d-ctor' );
```

#### tensor0d( \[dtype]\[, options] )

Returns a zero-dimensional [ndarray][@stdlib/ndarray/ctor] having a specified [data type][@stdlib/ndarray/dtypes].

```javascript
var getDType = require( '@stdlib/ndarray-dtype' );

var arr = tensor0d();
// returns <ndarray>

var dt = String( getDType( arr ) );
// returns 'float64'
```

By default, the function returns an [ndarray][@stdlib/ndarray/ctor] having a [`float64`][@stdlib/ndarray/dtypes] data type. To specify an alternative [data type][@stdlib/ndarray/dtypes], provide a `dtype` argument.

```javascript
var getDType = require( '@stdlib/ndarray-dtype' );

var arr = tensor0d( 'int32' );
// returns <ndarray>

var dt = String( getDType( arr ) );
// returns 'int32'
```

The function accepts the following options:

-   **order**: specifies whether an [ndarray][@stdlib/ndarray/ctor] is `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **readonly**: boolean indicating whether an array should be **read-only**. Default: `false`.

#### tensor0d( buffer\[, byteOffset]\[, dtype]\[, options] )

Returns a zero-dimensional [ndarray][@stdlib/ndarray/ctor] view of an [`ArrayBuffer`][@stdlib/array/buffer].

```javascript
var ArrayBuffer = require( '@stdlib/array-buffer' );
var getDType = require( '@stdlib/ndarray-dtype' );

var buf = new ArrayBuffer( 32 );

var arr1 = tensor0d( buf );
// returns <ndarray>

var dt1 = String( getDType( arr1 ) );
// returns 'float64'

var arr2 = tensor0d( buf, 'float32' );
// returns <ndarray>

var dt2 = String( getDType( arr2 ) );
// returns 'float32'

var arr3 = tensor0d( buf, 16 );
// returns <ndarray>

var dt3 = String( getDType( arr3 ) );
// returns 'float64'

var arr4 = tensor0d( buf, 16, 'float32' );
// returns <ndarray>

var dt4 = String( getDType( arr4 ) );
// returns 'float32'
```

#### tensor0d( value\[, dtype]\[, options] )

Creates a zero-dimensional [ndarray][@stdlib/ndarray/ctor] from a scalar value.

```javascript
var arr1 = tensor0d( 1.0 );
// returns <ndarray>

var arr2 = tensor0d( 1.0, 'float32' );
// returns <ndarray>
```

If a `dtype` argument is not provided and `value`

-   is a number, the default [data type][@stdlib/ndarray/dtypes] is the [default][@stdlib/ndarray/defaults] real-valued floating-point data type.
-   is a boolean, the default [data type][@stdlib/ndarray/dtypes] is the [default][@stdlib/ndarray/defaults] boolean data type.
-   is a complex number object of a known data type, the data type is the same as the provided value.
-   is a complex number object of an unknown data type, the default [data type][@stdlib/ndarray/dtypes] is the [default][@stdlib/ndarray/defaults] complex-valued floating-point data type.
-   is any other value type, the default [data type][@stdlib/ndarray/dtypes] is `'generic'`.

If `value` is a number and `dtype` is a complex [data type][@stdlib/ndarray/dtypes], the function returns a zero-dimensional [ndarray][@stdlib/ndarray/ctor] containing a complex number whose real component equals the provided scalar `value` and whose imaginary component is zero.

The function does not guard against precision loss when `value` is a number and the `dtype` argument is an integer [data type][@stdlib/ndarray/dtypes].

#### tensor0d.factory( dtype\[, options] )

Returns a function for creating a zero-dimensional [ndarray][@stdlib/ndarray/ctor].

```javascript
var getDType = require( '@stdlib/ndarray-dtype' );

var Float32Tensor0D = tensor0d.factory( 'float32' );

var arr = new Float32Tensor0D( 1.0 );
// returns <ndarray>

var dt = String( getDType( arr ) );
// returns 'float32'
```

The function supports the following parameters:

-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options (_optional_).

The function accepts the following options:

-   **order**: specifies whether the default memory layout for a returned [ndarray][@stdlib/ndarray/ctor] should be `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **readonly**: boolean indicating whether to return a **read-only** [ndarray][@stdlib/ndarray/ctor] by default. Default: `false`.

The function returned by the `factory` method supports the same arguments and options as `tensor0d` above, except for the `dtype` argument, as the returned function always returns a zero-dimensional [ndarray][@stdlib/ndarray/ctor] having the same [data type][@stdlib/ndarray/dtypes].

When providing options to the returned function, the provided option values override the defaults established during function creation.

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var discreteUniform = require( '@stdlib/random-array-discrete-uniform' );
var cartesianProduct = require( '@stdlib/array-cartesian-product' );
var unzip = require( '@stdlib/utils-unzip' );
var dtypes = require( '@stdlib/ndarray-dtypes' );
var logEachMap = require( '@stdlib/console-log-each-map' );
var tensor0d = require( '@stdlib/ndarray-tensor0d-ctor' );

// Create an array of random values:
var values = discreteUniform( 10, 5, 15, {
    'dtype': 'int32'
});

// Resolve a list of supported ndarray integer-valued data types:
var dts = dtypes( 'integer_and_generic' );

// Create value-dtype pairs:
var pairs = cartesianProduct( values, dts );

// Split the pairs into individual arguments:
var args = unzip( pairs );

// Define a callback to create an ndarray and return the scalar:
function clbk( value, dtype ) {
    var x = tensor0d( value, dtype );
    return x.get();
}

// Apply the callback and print the results:
logEachMap( 'value: %2d. dtype: %7s. value: %d.', args[ 0 ], args[ 1 ], clbk );
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-tensor0d-ctor.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-tensor0d-ctor

[test-image]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-tensor0d-ctor/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-tensor0d-ctor?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-tensor0d-ctor.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-tensor0d-ctor/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-tensor0d-ctor/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-tensor0d-ctor/main/LICENSE

[@stdlib/array/buffer]: https://github.com/stdlib-js/array-buffer

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes

[@stdlib/ndarray/defaults]: https://github.com/stdlib-js/ndarray-defaults

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
