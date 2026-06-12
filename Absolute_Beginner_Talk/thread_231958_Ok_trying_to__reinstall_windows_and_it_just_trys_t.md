---
title: "Ok trying to  reinstall windows and it just trys to load grub"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by DesertFox on 2006-08-08
it says booting from local disk...
GRUBloading stage 1.5
 Grubloading, please wait
error 17 even though windows it installed and i have cleared the hdd partions with fdisk

---

### Post by GuitarHero on 2006-08-08
You have to fix the master boot record with fdisk.

---

### Post by scxtt on 2006-08-08
if you have a bootable MS floppy, a simple **a:> format /mbr** will also work ...

---

### Post by dmizer on 2006-08-08
you didn't get everything then.  try using the repair mode offered in the windows install cd (or ubuntu's live cd), and use fdisk to make sure there are no partitions at all (everything should show freespace).

loading windows on top of linux overwrites the boot sector anyway, so even if you've neglected to delete your linux partitions, you should still be getting windows rather than grub.

do you have an actual windows install cd?  or do you just have recovery cd's?

---

### Post by bigken on 2006-08-08
boot from your winxp and go into repair console at the promt type fixmbr
then fixboot then exit reboot and you should be back into windows ;)

---

