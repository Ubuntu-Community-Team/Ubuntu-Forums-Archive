---
title: "Grub2 default os"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Streetwalker32 on 2007-03-17
I have ubuntu installed with xp.
How do I change the default os (which is loaded when timeout) ?

---

### Post by taurus on 2007-03-17
You change the "**default**" from "0" to whatever entry you want to boot after many seconds in /boot/grub/menu.lst.  Remember, each entry is counted as one and you start counting from 0.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

