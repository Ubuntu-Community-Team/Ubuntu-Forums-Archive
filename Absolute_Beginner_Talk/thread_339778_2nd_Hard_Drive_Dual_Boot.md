---
title: "2nd Hard Drive Dual Boot"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by mono-ireland on 2007-01-16
I am adding a second hard drive to my machine for Ubuntu...
How dow I make my machine dual boot...My current OS is XP.
Thanks

---

### Post by bunabattoir on 2007-01-16
Specify the second HDD for ubuntu installation (usually hdb). Install grub and edit its menu.lst. There is likely an example in the file.

---

### Post by ieee488 on 2007-01-16
Once GRUB is installed Windows XP will show up as one of the choices when you boot up.
If you want Windows XP to be the default, then and only then will you have to edit menu.lst.

---

