---
title: "PLEASE help a noob mount a Windows ME drive"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-09-03
I've got a possible bad hard drive that I need to pull data from in efforts to save the data.  The drive contains Windows ME (this is my buddy's drive).  I'm just not real sure how to go about it and its somewhat of an emergency.  Any advice you can provide as to how to mount this drive so that I may copy the data over would be GREATLY appreciated!!!  See below for some miscellaneous information regarding my current setup.  If you need me to post more information, just ask and I'll post ASAP!

The Windows ME drive below is bolded and in red...

_**This is what my drive/partition situation looks like:**_
Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1870    15020743+   7  HPFS/NTFS
/dev/hda2            1871        1882       96390   83  Linux
/dev/hda3            1883        3738    14908320    5  Extended
/dev/hda5            3557        3738     1461915   82  Linux swap / Solaris
/dev/hda6            2827        3555     5855661   83  Linux
/dev/hda7            1883        2825     7574584+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Red"]/dev/hdb1   *           1        2490    20000893+  44  Unknown[/COLOR]**


**_This is what my /etc/fstab looks like:_**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /boot           ext2    defaults        0       2
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222 0 0 defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bodhi.zazen on 2006-09-03
Try this:
```
sudo mkdir /mnt/windows
sudo mount /dev/hdb1 -t vfat /mnt/windows
```

---

