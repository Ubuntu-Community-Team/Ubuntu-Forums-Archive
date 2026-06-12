---
title: "Just set my pc up to dual boot and it keeps mounting my windows partition"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-28
Just set evrything up and it shows my windows partition on the desktop and it will not let me unmount it.

---

### Post by pnix on 2007-05-29
you can change this in /etc/fstab

---

### Post by maksei on 2007-05-29
to edit /etc/fstab you need to login as root:

sudo umount *path to your windows partition*

you can find the path by typing:
cat /etc/mtab


then edit the file with:
sudo gedit /etc/fstab

or

sudo nano /etc/fstab

---

