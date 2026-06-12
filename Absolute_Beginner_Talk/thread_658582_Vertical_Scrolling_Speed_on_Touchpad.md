---
title: "Vertical Scrolling Speed on Touchpad"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2008-01-04
How can I turn down the touchpad vertical scrolling speed on my laptop.  The default is insanely high and the mouse settings option doesn't have scrolling speed, only mouse sensitivity (as far as I can see).

---

### Post by iris-n on 2008-01-04
There's a program in the repositories that can do this. Called gsypnatics in the terminal, or just Touchpad in Add/Remove.

Be sure to add the line ```
        Option          "SHMConfig"             "on"

``` to your xorg.conf so that it works.

---

