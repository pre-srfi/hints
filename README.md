# SRFI nnn: hints

by Amirouche Boubekki, ...

## Status

Early Draft

## Abstract

??? abstract, preferably shorter than 200 words. Please outline the
need for, and design of, the proposal.

## Issues

??? Optional section that may point out things to be resolved. This
will not appear in the final SRFI.

## Rationale

??? detailed rationale. This should be 200-500 words long. Please
explain why the proposal should be incorporated as a standard feature
in Scheme implementations. List related standards and SRFIs, including
dependencies, conflicts, and replacements. If there are other
standards which this proposal will replace or with which it will
compete, please explain why the present proposal is a substantial
improvement.

### Survey of prior art

GitHub's version of Markdown can make tables. For example:

| System        | Procedure | Signature                 |
| ------------- |:---------:| ------------------------- |
| System A      | `jumble`  | _list_ _elem_             |
| System B      | `bungle`  | _elem_ _list_             |
| System C      | `frob`    | _list_ _elem_ _predicate_ |

## Specification

### `(hint-specification? obj) any? → boolean?`

Returns `#t` if `OBJ` is a valid hint specification. Otherwise returns `#f`.

`OBJ` may be:

- a predicate procedure;

- a list of predicate procedures;

- a list of predicate procedures where the last pair `cdr` is not the
  empty list, but a predicate procedure. In the latter case, the
  predicate that ends the list will be used to check the rest
  arguments;

- A list where items are valid according to the above rules.

### `(make-hint [documentation] arguments values raise) string? hint-specification? hint-specification? hint-specification → hint?` syntax

When `DOCUMENTATION` is absent. The implementation may construct a
documentation string based on `ARGUMENTS`, `VALUES` and `RAISE`.
Otherwise, the default value of `DOCUMENTATION` is the empty string.

Expand into a hint object.

### `(hint? obj)`

### `(hint-check-arguments? hint arguments) hint? list? → boolean?`

Given `HINT`, returns `#t` if `ARGUMENTS` are valid
arguments. `ARGUMENTS` are supposed to be all arguments passed to a
procedure including rest arguments. `ARGUMENTS` may be the empty list.

### `(hint-check-values? hint values) hint? list? → boolean?`

Given `HINT`, returns `#t` if `VALUES` are valid values. `VALUES` are
supposed to be all values returned by a procedure, hence `VALUES` may
be the empty list.

### `(hint-check-raise? hint obj) hint? any? → boolean?`

Given `HINT`, returns `#t` if `OBJ` is a valid object to raise.

### `(hint-documentation hint) hint? → string?`

Returns the documentation associated with `HINT`.

### `(hint [documentation] arguments values raise)` syntax

`hint` may appear anywhere a definition can appear. It may associate
`(make-hint DOCUMENTATION ARGUMENTS VALUES RAISE)` to the lexically
nearest previously defined lambda or procedure so that it is possible
to retrieve the documentation of the lambda or procedure from a REPL
e.g. using a `procedure-documentation` form.

## Examples

## Implementation

??? explanation of how it meets the sample implementation requirement
(see process), and the code, if possible, or a link to it Source for
the sample implementation.

## Acknowledgements

??? Give credits where credits is due.

## References

??? Optional section with links to web pages, books and papers that
helped design the SRFI.

## Copyright

Copyright (C) Firstname Lastname (20XY).

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
