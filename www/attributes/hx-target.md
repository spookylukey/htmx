---
layout: layout.njk
title: </> htmx - hx-target
---

## `hx-target`

The `hx-target` attribute allows you to target a different element for swapping than the one issuing the AJAX
request.  The value of this attribute can be:
 
 * a CSS query selector of the element to target
 * `this` which indicates that the element that the `hx-target` attribute is on is the target
 * `next <CSS selector>` which will scan the DOM forward for the first element that matches the given CSS selector. 
    (e.g. `next .error` will target the closest following sibling element with `error` class)
 * `previous <CSS selector>` which will scan the DOM backwards for the first element that matches the given CSS selector. 
    (e.g `previous .error` will target the closest previous sibling with `error` class)
 * `closest <CSS selector>` which will find the closest parent ancestor that matches the given CSS selector. 
    (e.g. `closest table` will target the closest parent table to the element)
 * `find <CSS selector>` which will find the first child descendant element that matches the given CSS selector.
    (e.g `find tr` will target the first child descendant row to the element)

Here is an example that targets a div:

```html
<div>
    <div id="response-div"></div>
    <button hx-post="/register" hx-target="#response-div" hx-swap="beforeend">
        Register!
    </button>
</div>
```

The response from the `/register` url will be appended to the `div` with the id `response-div`.

This example uses `hx-target="this"` to make a link that updates itself when clicked:
```html
<a hx-post="/new-link" hx-target="this" hx-swap="outerHTML">New link</a>
```

### Notes

* `hx-target` is inherited and can be placed on a parent element
