---
title: "External USB drive"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Bonnobo on 2007-04-25
I have just upgraded to Ubuntu 7.04 from 6.10, and I have discovered that my external USB drive has disappeared, where it was present in 6.10.  Can anyone help me to get it back?  Thanks.
But it is nice to know that SATA is now supported....:)

---

### Post by crispy_420 on 2007-04-25
How bout some more details about your drive?

Flash or hard drive?

Format?

---

### Post by Bonnobo on 2007-04-26
The Drive is a 320Gb Seagate External Hard disk.  Formatted in FAT32.

---

### Post by crispy_420 on 2007-04-26
Does the disc show up if you run this:

> fdisk -l

Maybe you just have some screwed up permissions? Try mounting as root and modify permissions.

---

### Post by Bonnobo on 2007-04-27
Disk /dev/sdc: 16 MB, 16220160 bytes
4 heads, 16 sectors/track, 495 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         494       15795+   1  FAT12

Disk /dev/sdf: 25 MB, 25690112 bytes
16 heads, 32 sectors/track, 98 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          98       25072    4  FAT16 <32M

This is the information I get...

So the system can see the drive.  Now how can get it so I can use it???  Please help:confused:

---

### Post by Pablo Pablovski on 2007-04-28
Hi! I had the same problem (although it was a Maxtor firewire drive). I found that the drive was being detected, but wasn't mounted in fstab, so wasn't accessible. Check you've still got a mount point.

My drive showed up in fdisk -l as  sdd1, so the fstab entry was:

/dev/sdd1 /media/external ntfs-3g defaults,locale=en_GB.utf8 0 0

HTH...

PP

---

