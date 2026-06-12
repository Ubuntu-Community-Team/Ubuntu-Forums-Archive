---
title: "trying to set up dual boot"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-04-18
had hardy set up on my 250gig, all set up and working properly, got a 500gig and pulled the 250gig clean out and set up ubuntu studio on the 500gig, now i have the cables to do the dual boot, but grub wont recognise the origional (hardy) hard drive.

sudo fdisk -l:

[sudo] password for mickpc:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006a08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30443   244533366   83  Linux
/dev/sda2           59294       60801    12113010    5  Extended
/dev/sda3   *       30444       59293   231737625   83  Linux
/dev/sda5           60048       60801     6056473+  82  Linux swap / Solaris
/dev/sda6           59294       60047     6056442   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9ea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29647   238139496   83  Linux
/dev/sdb2           29648       30401     6056505    5  Extended
/dev/sdb5           29648       30401     6056473+  82  Linux swap / Solaris



help

---

### Post by bumanie on 2008-04-18
Because you installed ubuntu studio, without the 250g drive installed in the computer, grub won't know that there is a second drive it has to worry about. Could you post the output of>  cat /boot/grub/menu.lst and > cat /etc/fstab I think both will need editing or else reinstall ubuntu studio with the 250g drive plugged into the computer (that's probably easier IMO if ubuntu studio is a brand new installation).

---

### Post by Mick8882003 on 2008-04-18
yea im thinking the same now.
ok its done lol

---

