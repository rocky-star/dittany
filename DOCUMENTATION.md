# Dittany Documentation
Although Dittany is already ready-made, it provides various CSS classes
to enrich the experience of your EPUB documents. This document contains
detailed descriptions for all customization variables, classes, and
element styles.

## Block Elements

### Paragraphs
By default, paragraphs don't have any special styling. If a CJK writing
system has been specified, first-line indentations will be applied to
every paragraph.

### Headings
Different heading styles will be applied to heading elements according
to specified classes on `<body>` elements. See the
"[Sections](#sections)" section for more information.

The following table shows heading styles used in different levels of
book divisions:

| Book division | `<h1>` | `<h2>` | `<h3>` | `<h4>` | `<h5>` |
|---------------|--------|--------|--------|--------|--------|
| Chapter       | 1st    | 2nd    | 3rd    | 4th    | 5th    |
| Section       | 2nd    | 3rd    | 4th    | 5th    | *none* |
| Subsection    | 3rd    | 4th    | 5th    | *none* | *none* |
| Subsubsection | 4th    | 5th    | *none* | *none* | *none* |
| Subsubsection | 5th    | *none* | *none* | *none* | *none* |

### Alternative Styling of Chapter Headings
You can specify an alternative style for chapter headings. The following
list shows different alternative styles and their visuals:

* `a` class: darker red text, right alignment
* `b` class: green text, centered
* `c` class: darker yellow text, left alignment, with bottom border
* `d` class: blue text, left alignment, with bottom border

## Book Divisions

### Regular Divisions (Chapters)
Regular divisions don't need any CSS classes on `<body>` elements. In
these divisions, the styling of headings follow the standard behavior.

### Sections
The following table shows divisions like sections, subsections, etc.,
and corresponding CSS classes:

| Division         | CSS class |
|------------------|-----------|
| Chapter          | *none*    |
| Section          | `sect1`   |
| Subsection       | `sect2`   |
| Subsubsection    | `sect3`   |
| Subsubsubsection | `sect4`   |

### Copyright Pages
To specify a copyright page, add the `copyright-page` CSS class to the
corresponding `<body>` element. Headings in copyright pages have special
styling.

## Inline Elements

### Mixing western script text and CJK text
If your EPUB document is written in CJK script, wrap mixed western text
in `<span class="w">` if possible, especially in elements with special
typefaces applied. The following list shows elements and styles that's
**strongly recommend** to wrap mixed western text with `<span>`:

* Bare `<h4>`, `<h3>` in sections, `<h2>` in subsections, `<h1>` in
  subsubsections
* Bare `<h5>`, `<h4>` in sections, `<h3>` in subsections, `<h2>` in
  subsubsections, `<h1>` in subsubsubsections

## Customization
To customize Dittany, the first thing you need is a SCSS file that
contains required customization variables and a `@use` rule for loading
the actual Dittany style sheet. After compilation, the output file will
contains Dittany with appropriate rules.

A example customization style sheet may looks like:

``` scss
$script: "Latn";
// (other customization variables)
@use "dittany"
```

Rest contents of this section describes supported customization
variables.

### `$script`
The `$script` variable specifies the writing system of the EBUB
document. Appropriate font combinations and settings (e.g., first-line
indentation, etc.) will be used according to the specified writing
system.

The following table shows all possible values:

| Value            | Description        |
|------------------|--------------------|
| `"Hans"`         | Simplified Chinese |
| all other values | Latin script       |

Although non-matching values will be interpreted as Latin script,
prefer use `"Latn"` for Latin, since Dittany may add support for more
writing systems in future.
