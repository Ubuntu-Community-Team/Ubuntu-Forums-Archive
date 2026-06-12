---
title: "Where is the Boot Menu?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-03-25
Hello!

I have a PC with 2 Partitions:

1. Windows NTFS Empty Partition
2. Windows XP Pro OS

I booted from the Ubuntu v7.04 Feisty Beta CD & installed Feisty Beta on # 1 above.

Whenever I boot my PC, I don't get to any Boot Menu, but my PC boots automatically to the Ubuntu OS.
I want to be able to choose on which OS my PC will boot at Startup...

Thanks.

---

### Post by taurus on 2007-03-25
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and increase the **timeout** to something longer.  Then, remove the # in front of **hidemenu** so you would get a menu to choose which OS to boot from.

---

