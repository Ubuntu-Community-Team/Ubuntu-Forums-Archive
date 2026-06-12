---
title: "Dual Boot OS's"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by waynehapp on 2007-05-20
I have a machine with 2 hard drives. One has RedHat 5 and the other Ubuntu.  In the installation process they seem to disable the others grub info. I say disable because i can use "Super Grup" to go between them. Can anyone point me to some instructions on how to get them on the same boot menu?

Wayne

---

### Post by Nekiruhs on 2007-05-20
```
gksudo gedit /boot/grub/menu.lst
```
That will open your menu.lst, the file that controls your grub menu, now the file is heavily commented and im not at my Ubuntu box right now, so read the comments and it should tell you what you need to add.

---

