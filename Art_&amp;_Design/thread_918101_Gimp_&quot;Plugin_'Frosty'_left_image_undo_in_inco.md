---
title: "Gimp: &quot;Plugin 'Frosty' left image undo in inconsistant state...&quot;"
date: 2008-09-12
forum: Art &amp; Design
---

### Post by diablo75 on 2008-09-12
I'm trying to use the Alpha to Logo effect "Frosty" in Gimp, and it's worked for me in the past but suddenly crashes now when I try to use it.  This isn't the first time I've used this effect, but it's never crashed on me before.  I even tried to restart the PC to see if I could kick it, but that didn't help any.  Is there something else I could try to get this particular plugin to function properly again?

The first error message I see says "Plugin 'Frosty" left image undo in inconsistent state, closing open undo groups."

A separate box later shows up:

Error while executing
(script-fu-frosty-logo-alpha 1 6 100 '(14 9 5))

Error: Procedure execution of gimp-edit-stroke failed

---

### Post by diablo75 on 2008-09-14
Bump.  How might I fix this problem?

---

### Post by Half-Left on 2008-09-14
What exactly are you applying the plugin to?, 

Make a new layer, make sure you selected it, make a square with the select tool, fill it,apply Frosty

---

### Post by diablo75 on 2008-09-14
> **Half-Left said:**
> What exactly are you applying the plugin to?, 

Make a new layer, make sure you selected it, make a square with the select tool, fill it,apply Frosty

I did as you said and the same error was produced.

What was originally attempting to apply the plugin to was text.  I did Text (typed stuff)> Alpha to Selection> Copy> New Layer> Paste> Alpha to selection again> Frosty > FAIL.

GOOD NEWS THOUGH.....  I just reinstalled Gimp and the plugin works now.
:guitar:

---

