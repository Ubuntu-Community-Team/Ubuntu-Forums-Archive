---
title: "can't save Open Office file in FAT32 disc"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by FariAzz on 2006-08-05
I have a FAT32 partition and Open Office won't let me save new files in that partition. It only lets me save changes to files that were already there. 

The exact message I get when trying to save a new document into the FAT32 partition is "Saving using protocol media is not supported"

---

### Post by tseliot on 2006-08-05
please post the content of your /etc/fstab

---

### Post by FariAzz on 2006-08-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by FariAzz on 2006-08-05
hda5 is the drive where I try to save new documents and it doesn't work.

---

### Post by FariAzz on 2006-08-05
the exact message I get when trying to save a new document into the FAT32 partition is "Saving using protocol media is not supported"

---

