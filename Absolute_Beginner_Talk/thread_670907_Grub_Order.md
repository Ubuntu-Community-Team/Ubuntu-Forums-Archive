---
title: "Grub Order"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Law506 on 2008-01-18
I am searching for the way to change the order of GRUB to where I can have other OS's come before Ubuntu.

Thanks in advance.

---

### Post by chewearn on 2008-01-18
Edit the file: /boot/grub/menu.lst

In terminal:
```
sudo gedit /boot/grub/menu.lst
```To change the default boot, change value for "default 0" to something else:
default 1 for the second item in the menu
default 2 for the third item in the menu, and so on

To change the order of items themselves, you have to shuffle each "stanza" of the menu entries.  However, do not change items within "DEBIAN AUTOMAGIC KERNELS LIST" (unless you know what you are doing).  Just move items around that section.

---

