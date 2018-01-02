# JavaScript Examples

> [remark][remark] plugin to run JavaScript examples.

<section class="usage">

## Usage

```javascript
var run = require( '/path/to/@stdlib/tools/remark/plugins/remark-run-javascript-examples' );
```

#### run()

Attaches a [remark][remark] plugin which, when provided a Markdown abstract syntax `tree`, runs JavaScript examples.

```javascript
var remark = require( 'remark' );

var str = '<section class="examples">\n\n## Examples\n\n```javascript\nconsole.log( "HELLO WORLD!" );\n```\n\n</section>\n\n<!-- /.examples -->';

remark().use( run ).process( str, done );

function done( error ) {
    if ( error ) {
        throw error;
    }
}
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   When processing a Markdown abstract syntax tree (AST), the plugin scans the tree for `section` elements with the class `examples`. For example,

    <!-- lint disable code-block-style -->

        <section class="examples">

        ## Examples

        ```javascript
        console.log( 'HELLO WORLD' );
        ```

        </section>

        <!-- /.examples -->

    Upon finding an examples section, the plugin scans for JavaScript fenced code blocks. For each JavaScript code block, the plugin extracts example code and runs that code in a separate child process.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint-disable no-sync -->

<!-- eslint no-undef: "error" -->

```javascript
var join = require( 'path' ).join;
var remark = require( 'remark' );
var readSync = require( 'to-vfile' ).readSync;
var run = require( '/path/to/@stdlib/tools/remark/plugins/remark-run-javascript-examples' );

// Load a Markdown file:
var fpath = join( __dirname, 'examples', 'fixtures', 'simple.txt' );
var file = readSync( fpath, 'utf8' );

// Run examples:
remark().use( run ).process( file, done );

function done( error ) {
    if ( error ) {
        throw error;
    }
}
```

</section>

<!-- /.examples -->

<section class="links">

[remark]: https://github.com/wooorm/remark

</section>

<!-- /.links -->