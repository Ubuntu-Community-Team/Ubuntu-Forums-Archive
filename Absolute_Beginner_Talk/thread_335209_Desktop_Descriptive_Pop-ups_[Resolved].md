---
title: "Desktop Descriptive Pop-ups [Resolved]"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tonester on 2007-01-10
Hi,

When the mouse pointer hovers over a program icon on my desktop long enough, a popup description appears next to the pointer (for example,  holding the pointer over the Firefox icon brings up a popup that reads" Firefox Web Browser Browse the World Wide Web").

Is there a way of turning these popup descriptions off?

TIA

---

### Post by macogw on 2007-01-10
You can right click and hit properties and backspace out the name and comment sections

---

### Post by tonyr1988 on 2007-01-10
Try this:

-Open a terminal (Applications -> Accessories -> Terminal)
-Type

> gconf-editor

-In the left pane, navigate to apps -> panel -> global
-In the right pane, scroll down and find "tooltips_enabled" and un-check the checkbox to the right of it.
-Close the gconf-editor and your Terminal

See if that works.

---

### Post by tonester on 2007-01-10
The gconf-editor route did the trick - 

Thanks for the replies!

---

