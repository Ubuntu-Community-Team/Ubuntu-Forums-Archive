---
title: "Apple+c apple+v"
date: 2010-12-12
forum: Apple Hardware Users
---

### Post by antarello on 2010-12-12
Is it possible to have the same keyboard shortcuts as apple+c to copy, apple+t to have a new tab in chromium and so on?

---

### Post by NoBugs! on 2010-12-12
The Apple key shows up as "Windows" key or "Super" shift in Linux, you can change this using xmodmap, for example:
```
clear control
clear mod4

keycode 37 = Control_L
keycode 134 = Control_R
!### change 134 to 116 if using ubuntu hardy, not ibex. ###
add control = Control_L Control_R

add mod4 = Super_L

```

---

