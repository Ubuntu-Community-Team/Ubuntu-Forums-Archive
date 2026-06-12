---
title: "Copying downloaded files on a floppy"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by pkj on 2007-06-26
Basic problems....

How do i copy something downloaded and available on the desktop onto a floppy.

Thereafter the floppy has to be used in a windows machine

pkj

---

### Post by alienexplorers on 2007-06-26
you have to first mount the floppy then you can copy to it.

Insert this line in your /etc/fstab folder.
run    gksudo gedit /etc/fstab

> /dev/fd0        /media/floppy   vfat    rw,user,noauto  0       0

This works if you are keeping the floppy as Fat32

---

