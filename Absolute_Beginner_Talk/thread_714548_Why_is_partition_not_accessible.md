---
title: "Why is partition not accessible?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-03-03
Hi everyone
I noticed that one of my partition can't be utilized. I can't create anything, but I could go into it, (it's empty). When I go to my /media folder, it shows as sda2 and there's a little lock at the bottom right corner of the icon. How do i enable in my system?

---

### Post by disappearedng on 2008-03-03
By the way this is my fstab

"
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=23262e0e-2291-488c-95cb-3c6f5ab556c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1266AFEC66AFCF33 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=80C2F69090FA0800 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=000EE7970EE7844E /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=1ecd7755-3886-45b7-b0ae-97d7ba3bf5a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
" 
Where sda2 is the partiion that i want to access.

---

### Post by disappearedng on 2008-03-10
Any Ideas?

---

### Post by NightwishFan on 2008-03-10
Try running nautilus as super user. Press alt+f2 and type:
gksudo nautilus

Also check the permissions for the drive.

---

### Post by angry_johnnie on 2008-03-10
have you tried using ntfs-config?  It's available in your repositories, and it will allow you to access ntfs partitions with read/write privileges.

---

### Post by prshah on 2008-03-10
> **disappearedng said:**
> Hi everyone
I noticed that one of my partition can't be utilized. I can't create anything, but I could go into it, (it's empty). When I go to my /media folder, it shows as sda2 and there's a little lock at the bottom right corner of the icon. How do i enable in my system?

That's probably an extended partition. You cannot utilise an extended partition, you can only create logical drives in it that will show up as sda5,6,7...

To confirm, in a terminal run the command:

sudo fdisk /dev/sda

then "p" for print table:

The type of sda2 will be set as Win95/Extd or something similar. If not, please post your fdisk "p" output here. Use "q" to quit

DONT muck around with the extended partition, or you WILL lose the downstream partitions, which start numbering from sda5.

Cheers,
PRShah

---

