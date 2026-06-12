---
title: "Boot Manager default to XP"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by jamski on 2007-02-27
On my XP/Ubuntu 6.10 machine, is there a way to make the boot manager default to XP instead of Ubuntu if nothing is selected?

---

### Post by Adramelech on 2007-02-27
edit /boot/grub/menu.lst
and change the default line to the number of the xp entry, entries are numbered from 0 so if winxp is in 3rd place in the grub menu then u change the line to,:
default 2

---

