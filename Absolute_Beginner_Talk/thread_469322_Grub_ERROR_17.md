---
title: "Grub ERROR 17"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by ianchen06 on 2007-06-09
i installed Ubuntu and grub on (hd1) because this is not my computer, but after i installed it and booted in to the slave drive (hd1) it appeared "ERROR 17   can not mount the selected partition", how do i solve this??

---

### Post by logos34 on 2007-06-10
> **ianchen06 said:**
> i installed Ubuntu and grub on (hd1) because this is not my computer, but after i installed it and booted in to the slave drive (hd1) it appeared "ERROR 17   can not mount the selected partition", how do i solve this??

It may be that although the slave was (hd1) at install time, when you moved it to first position in the hard disk boot priority, it became (hd0) -- this happens with installs to external usn hard drives.  You have to change all instances in menu.lst of '(hd1,x)' to '(hd0,x)',  as well as change device,map file.  Or else it has to do with the way the drives are being detected by the BIOS.  See this [thread ]("http://ubuntuforums.org/showthread.php?t=442945")(includes a link to Herman's Super GRub disk page).

---

