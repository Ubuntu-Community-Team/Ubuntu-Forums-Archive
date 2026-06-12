---
title: "Fstab does not see my windows drive"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by dj1120 on 2006-12-30
Hi all , I am running ubuntu 6.10 and I currently am dual booting on 2 separate hard drives (Both are sata xp is on a 250 gb drive and edgy is on a 400 gb drive) I am trying to see my windows partition so that I can read/write to it to pull my media files into ubuntu and vice versa (possibly with ntfs-3g) when I run fdisk-l this is what I get:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48264   387680548+  83  Linux
/dev/sda2           48265       48641     3028252+   5  Extended
/dev/sda5           48265       48641     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   7  HPFS/NTFS
 
When I go to edit my Fstab I see :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=92f69255-22dc-4ca0-8f8c-30149294fc76 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f3b7f2c8-802c-4710-a10e-bd3ca812fb3e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
 
If I read the fdisk output write my ntfs drive is /dev/sdb1 but I dont see it in fstab. How do I put there? 
Also how do I set the permissions so that ntfs-3g will mount it?

Thanks

---

### Post by taurus on 2006-12-30
If you want to write to your ntfs, then you need to follow this guide here...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

