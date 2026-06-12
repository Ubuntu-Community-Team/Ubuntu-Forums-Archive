---
title: "GIMP script-fu: how do I call a function that appears in the keybindings"
date: 2009-07-04
forum: Art &amp; Design
---

### Post by Cracauer on 2009-07-04
I'm writing some script-fu scheme and I cannot figure out how to call some things. 

Let's say I want to create a new view from my function:

```

(define (cra-view-0)
  (view-new))

```

"view-new" is what appears as function name in the keybindings editor.  But alas this doesn't work, this symbol is not defined in scheme.

I then went and tried
(gimp-view-new)
but that isn't defined either.

Is there any way to reliably call functions when you see their symbols in key bindings? Maybe there's a may to call them by menu hierarchy? E.g.  (call-menu-stuff "View/New") or something like that?

---

