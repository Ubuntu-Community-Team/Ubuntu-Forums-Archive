---
title: "Change font size in Firefox bookmarks tool bar"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-05-05
Is there any way to change the size of the fonts in the Firefox bookmarks tool bar?

---

### Post by kerry_s on 2007-05-05
you can use a ~.mozilla/firefox/?.default/chrome/userChrome.css, adjust size and font to your needs. it's a hidden file in your home(ctrl+h) you create it like the example.

```
tree {
font-family: verdana !important;
font-size: 8pt !important;
}
```

Mine->

```
/*
 * Edit this file and copy it as userChrome.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */

/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*
 * Make menu items in particular 15 pt instead of the default size:
 *
 * menupopup > * {
 *   font-size: 15pt !important
 * }
 */
/*
 * Give the Location (URL) Bar a fixed-width font
 *
 * #urlbar {
 *    font-family: monospace !important;
 * }
 */

/*
 * Eliminate the throbber and its annoying movement:
 *
 * #throbber-box {
 *   display: none !important;
 * }
 */

/*
 * For more examples see http://www.mozilla.org/unix/customizing.html
 */


#urlbar {
-moz-appearance: none !important;
-moz-border-radius: 3px !important;
padding-right: 1px !important;
}


 /* Make inactive tabs hardly visible */
#content tab:not([selected="true"]) {
    -moz-opacity: 0.3 !important; }


/* Remove the forward and back button dropdown arrows */
#back-button .toolbarbutton-menubutton-dropmarker,
#forward-button .toolbarbutton-menubutton-dropmarker {
  display: none !important; }


/* Multi-row bookmarks toolbar */
#bookmarks-ptf {display:block}
#bookmarks-ptf toolbarseparator { display:inline }


window {
font-family: verdana !important;
font-size: 8pt !important;
}


tree {
font-family: verdana !important;
font-size: 8pt !important;
}


```

---

