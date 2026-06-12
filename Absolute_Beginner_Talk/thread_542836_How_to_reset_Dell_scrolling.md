---
title: "How to reset Dell scrolling"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Bronx85 on 2007-09-04
I believe I accidentally disabled the touch pad ability to scroll horizontally and vertically (using far rigt-side or bottom of touchpad).  Any help on how to re-set this?

---

### Post by nick_h on 2007-09-05
Touchpad functionality is defined in an *InputDevice* section in your */etc/X11/xorg.conf* file.

Look for the synaptics driver.  To get details of the options available type:
```
man synaptics
```

---

