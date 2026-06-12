---
title: "grub loader question"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by jaskah on 2006-06-15
hello
i have windows xp and two installs of ubuntu hoary on my computer (one install is only for work with audio;one for my girlfriend).
how can i determine the order of which operating system appears first in the grub loader window? is there a config file for this somewhere?
any help is greatly appreciated.
jason

---

### Post by bruenig on 2006-06-15
```
sudo gedit /boot/grub/menu.lst
```

when you get in there you can cut and paste each entry around to whatever order you want it to display

---

### Post by bruce89 on 2006-06-15
> **jaskah]hello
i have windows xp and two installs of ubuntu hoary on my computer (one install is only for work with audio said:**
> 
First, hoary is anchient now, and second why do you need 2 installs, you can have more than 1 user on any install.  Anyway do this ```
sudo gedit /boot/grub/menu.lst
```  Near the top, there should be a bit with [QUOTE]# array will desync and will not let you boot your system.
default		0

## timeout sec
set 0 to the number in the list you want to be default.

---

### Post by jaskah on 2006-06-15
thanks!

---

### Post by bruce89 on 2006-06-15
No problem.

---

