---
title: "New to Ubuntu"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by hitmanzz on 2007-05-23
So i just installed Ubuntu 7.04 the latest version.

while installing i wanted to install it on my 40 gig slave drive, i checked it and not my master drive, i divided the slave into 2 partitions, one for regular usage, and one for swap like the pop up warned me about, after installing it and removing the disc. Ubuntu loaded up, i opened My Computer and it doesn't show my 40 gig drive but instead shows my master slave with all my windows stuff. did i do anything wrong during the installation?

---

### Post by drowner on 2007-05-23
> **hitmanzz said:**
> So i just installed Ubuntu 7.04 the latest version.

while installing i wanted to install it on my 40 gig slave drive, i checked it and not my master drive, i divided the slave into 2 partitions, one for regular usage, and one for swap like the pop up warned me about, after installing it and removing the disc. Ubuntu loaded up, i opened My Computer and it doesn't show my 40 gig drive but instead shows my master slave with all my windows stuff. did i do anything wrong during the installation?

No, i doubt it.

If you installed ubuntu to the OTHER drive, and you are now running ubuntu, the drive is still there. I suspect you may be having difficulty with understanding the linux filesystem, but first, lets check your hard drives.
Post us the output of the following commands in a terminal window:
```

sudo fdisk -l
``` This command tells us which disks and partitions linux can see

and then

```
cat /etc/fstab
```
This command tells us the contents of your 'fstab' file, which contains info on where linux has 'mounted' your partitions and drives, ie, where on your filesystem you can access them from

---

### Post by hitmanzz on 2007-05-25
after entering in sudo fdisk -l 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3647    29294496   83  Linux
/dev/hdb2            3648        4865     9783585   82  Linux swap / Solaris


then cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=900613ad-87d7-4ee9-acf5-e31f0e909fc6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=BEE84B98E84B4DB9 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=42799072-9d91-4382-ab07-27ea720ac3e7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

