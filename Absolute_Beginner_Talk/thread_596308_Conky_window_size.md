---
title: "Conky window size?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by volksman on 2007-10-29
Is there a way to adjust the conky window size?  I used a conf that was offset by 240 px.  I'm wondering if I can remove the offset and just set the window to the right size.

Any ideas?

---

### Post by taurus on 2007-10-29
You can do that in ~/.conkyrc.

Applications -> Accessories -> Terminal
```
gedit ~/.conkyrc
```

---

### Post by volksman on 2007-10-29
Yes but what specifically in the rc file changes the window size..I don't see anything specific to size in there....

---

### Post by corney91 on 2007-10-29
minimum_size and maximum_width should work.
For example, in mine:
minimum_size 180 5
maximum_width 180

Where 180 is both the maximum and minimum width and 5 is the minimum height.

---

