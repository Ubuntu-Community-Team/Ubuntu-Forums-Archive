---
title: "2nd ntfs drive not recognised; trying....."
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by pgirard on 2007-03-13
Ubuntu 6.10 - the Edgy Eft

Here is what I have:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1797    14434371   83  Linux
/dev/hda2            3424        3649     1815345    5  Extended
/dev/hda3   *        1798        3423    13060845   83  Linux
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris
/dev/hda6            3424        3497      594342   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661    7  HPFS/NTFS

I'm trying to get hdb to be read and written to. I'm out of answers.

It has all my family photos on it. If I cant get this to work, I may pack it up and go back...

---

### Post by Famicommie on 2007-03-13
Try these instructions: [http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/](http://opensourceroolz.wordpress.com/2007/02/26/writing-to-windows-ntfs/)

---

