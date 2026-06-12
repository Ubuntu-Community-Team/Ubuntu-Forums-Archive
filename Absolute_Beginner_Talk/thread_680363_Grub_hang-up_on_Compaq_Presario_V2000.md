---
title: "Grub hang-up on Compaq Presario V2000"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Moutain on 2008-01-27
I just installed generic 7.04 from the official book on my Compaq Presario V2000 and on boot GRUB snags and requires Escape.  How can I get it to just go right to th elog on screen.  The messag I get is:

GRUB Loading stage1.5.


BRUB loading, please wait...
Press 'ESC' to enter the menu... 2




It will go on to the menu when I press escape, but not a very clean way to get started.

Thanks,

---

### Post by dcstar on 2008-01-28
> **Moutain said:**
> I just installed generic 7.04 from the official book on my Compaq Presario V2000 and on boot GRUB snags and requires Escape.  How can I get it to just go right to th elog on screen.  The messag I get is:

GRUB Loading stage1.5.


BRUB loading, please wait...
Press 'ESC' to enter the menu... 2




It will go on to the menu when I press escape, but not a very clean way to get started.

Thanks,
In a terminal:
```
gksudo gedit /boot/grub/menu.lst
```
and change the setting for the menu.

---

