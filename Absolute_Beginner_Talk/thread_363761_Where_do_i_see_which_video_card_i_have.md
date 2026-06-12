---
title: "Where do i see which video card i have?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-17
i've just installed Ubuntu on another computer on which i don't know which video card i have.
i know it's ATI ,but that's all.
how do i find out what model it is?

---

### Post by divague on 2007-02-17
open a terminal and run

$more /etc/X11/xorg.conf

and look in the device section

---

### Post by taurus on 2007-02-17
```
lspci
```

---

