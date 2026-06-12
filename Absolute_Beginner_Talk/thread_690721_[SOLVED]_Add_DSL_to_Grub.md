---
title: "[SOLVED] Add DSL to Grub"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-02-07
earleir i installed DSL alongside Xubuntu on my laptop.

however i didnt choose to install Lilo. I like GRUB.

how do i add DSL to the grub menu?

---

### Post by talsemgeest on 2008-02-08
Try modifying the menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by skymera on 2008-02-08
yeah solved now, flicked through another thread and gave me some clues :)

---

### Post by talsemgeest on 2008-02-08
Glad to hear it :)

---

