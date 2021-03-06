# mixitup.Config

## Overview

The MixItUp configuration object is extended with properties relating to
the Pagination extension.

For the full list of configuration options, please refer to the MixItUp
core documentation.

### Contents

- [classNames](#classNames)
- [load](#load)
- [pagination](#pagination)
- [render](#render)
- [selectors](#selectors)
- [templates](#templates)


<h2 id="classNames">classNames</h2>

A group of properties defining the output and structure of class names programmatically
added to controls and containers to reflect the state of the mixer.

### elementPager




The "element" portion of the class name added to pager controls.


|Type | Default
|---  | ---
|`string`| `'control'`

###### Example: changing the `config.classNames.elementPager` value

```js

// Change from the default value of 'control' to 'pager'

var mixer = mixitup(containerEl, {
    classNames: {
        elementPager: 'pager'
    }
});

// Base pager output: "mixitup-pager"
```
### elementPageList




The "element" portion of the class name added to the page list element, when it is
in its disabled state.

The page list element is the containing element in which pagers are rendered.


|Type | Default
|---  | ---
|`string`| `'page-list'`

###### Example: changing the `config.classNames.elementPageList` value

```js

// Change from the default value of 'page-list' to 'pagination-links'

var mixer = mixitup(containerEl, {
    classNames: {
        elementPageList: 'pagination-links'
    }
});

// Disabled page-list output: "mixitup-pagination-links-disabled"
```
### elementPageStats




The "element" portion of the class name added to the page stats element, when it is
in its disabled state.

The page stats element is the containing element in which information about the
current page and total number of pages is rendered.


|Type | Default
|---  | ---
|`string`| `'page-stats'`

###### Example: changing the `config.classNames.elementPageStats` value

```js

// Change from the default value of 'page-stats' to 'pagination-info'

var mixer = mixitup(containerEl, {
    classNames: {
        elementPageList: 'pagination-info'
    }
});

// Disabled page-list output: "mixitup-pagination-info-disabled"
```
### modifierFirst




The "modifier" portion of the class name added to the first pager in the list of pager controls.


|Type | Default
|---  | ---
|`string`| `'first'`

### modifierLast




The "modifier" portion of the class name added to the last pager in the list of pager controls.


|Type | Default
|---  | ---
|`string`| `'last'`

### modifierLast




The "modifier" portion of the class name added to the previous pager in the list of pager controls.


|Type | Default
|---  | ---
|`string`| `'prev'`

### modifierNext




The "modifier" portion of the class name added to the next pager in the list of pager controls.


|Type | Default
|---  | ---
|`string`| `'next'`

### modifierTruncationMarker




The "modifier" portion of the class name added to truncation markers in the list of pager controls.


|Type | Default
|---  | ---
|`string`| `'truncation-marker'`


<h2 id="load">load</h2>

A group of properties defining the initial state of the mixer on load (instantiation).

### page




An integer defining the starting page on load, if a page limit is active.


|Type | Default
|---  | ---
|`number`| `1`

###### Example: Defining a start page other than 1 to be applied on load

```js

// The mixer will show page 3 on load, with 8 items per page.

var mixer = mixitup(containerEl, {
    pagination: {
        limit: 8
    },
    load: {
        page: 3
    }
});
```

<h2 id="pagination">pagination</h2>

A group of properties defining the mixer's pagination behavior.

### generatePageList




A boolean dictating whether or not MixItUp should render a list of pager controls.

If you wish to control pagination functionality via the API, or your own UI, this can be set to `false`.

In order for this functionality to work, you must provide MixItUp with a `pageList`
element matching the selector defined in `selectors.pageList`. Pager controls will be
rendered inside this element as per the templates defined for the `templates.pager`
and related configuration options, or if set, a custom render
function supplied to the `render.pager` configuration option.


|Type | Default
|---  | ---
|`boolean`| `true`

### generatePageStats




A boolean dictating whether or not MixItUp should render a stats about the
current page (e.g. "1 to 4 of 16").

In order for this functionality to work, you must provide MixItUp with a `pageStats`
element matching the selector defined in `selectors.pageStats`. Page stats content will
be rendered inside this element as per the templates defined for the `templates.pageStats`
and `templates.pageStatsSingle` configuration options, or if set, a custom render
function supplied to the `render.pageStats` configuration option.


|Type | Default
|---  | ---
|`boolean`| `true`

### maintainActivePage







|Type | Default
|---  | ---
|`boolean`| `true`

### loop







|Type | Default
|---  | ---
|`boolean`| `false`

### hidePageListIfSinglePage







|Type | Default
|---  | ---
|`boolean`| `false`

### hidePageStatsIfSinglePage







|Type | Default
|---  | ---
|`boolean`| `false`

### limit







|Type | Default
|---  | ---
|`number`| `-1`

### maxPagers




A number dictating the maximum number of individual pager controls to render before
truncating the list.


|Type | Default
|---  | ---
|`number`| `5`


<h2 id="render">render</h2>

A group of optional render functions for creating and updating elements.

### pager




A function returning an HTML string representing a single pager control element.

By default, MixItUp will render pager controls using its own internal renderer
and templates (see `templates.pager`), but you may override this functionality by
providing your own render function here instead. All pager elements must have a
data-page element indicating the action of the control.

The function receives an object containing all neccessary information
about the pager as its first parameter.


|Type | Default
|---  | ---
|`function`| `'null'`

### pageStats




A function returning an HTML string forming the contents of the "page stats" element.

By default, MixItUp will render page stats using its own internal renderer
and templates (see `templates.pageStats`), but you may override this functionality by
providing your own render function here instead.

The function receives an object containing all neccessary information
about the current page and total pages as its first parameter.


|Type | Default
|---  | ---
|`function`| `'null'`


<h2 id="selectors">selectors</h2>

A group of properties defining the selectors used to query elements within a mixitup container.

### pageList




A selector string used to query the page list element.

Depending on the value of `controls.scope`, MixItUp will either query the
entire document for the page list element, or just the container.


|Type | Default
|---  | ---
|`string`| `'.mixitup-page-list'`

### pageStats




A selector string used to query the page stats element.

Depending on the value of `controls.scope`, MixItUp will either query the
entire document for the page stats element, or just the container.


|Type | Default
|---  | ---
|`string`| `'.mixitup-page-stats'`


<h2 id="templates">templates</h2>

A group of template strings used to render pager controls and page stats elements.

### pager







|Type | Default
|---  | ---
|`string`| `'<button type="button" class="${classNames}" data-page="${pageNumber}">${pageNumber}</button>'`

### pagerPrev







|Type | Default
|---  | ---
|`string`| `'<button type="button" class="${classNames}" data-page="prev">&laquo;</button>'`

### pagerNext







|Type | Default
|---  | ---
|`string`| `'<button type="button" class="${classNames}" data-page="next">&raquo;</button>'`

### pagerTruncationMarker







|Type | Default
|---  | ---
|`string`| `'<span class="${classNames}">&hellip;</span>'`

### pageStats







|Type | Default
|---  | ---
|`string`| `'${startPageAt} to ${endPageAt} of ${totalTargets}'`

### pageStatsSingle







|Type | Default
|---  | ---
|`string`| `'${startPageAt} of ${totalTargets}'`

### pageStatsFail







|Type | Default
|---  | ---
|`string`| `'None found'`


