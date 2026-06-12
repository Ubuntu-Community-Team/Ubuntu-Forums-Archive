---
title: "CD/DVD drive mounting issues"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2006-10-09
for some reason, it seems all of a sudden, i cant mouuntcds or dvds, when i try to open the dvds in movie player it tells me : could not find mount point for /dev/hdb which is my cd/dvdrom drive. when i try to open disks the drive just goes crazy for a bit but i cant read any data and it doesnt, as it has in the past, automatically stick a disk icon on to the desktop for me. i havent changed anything settings wise since i upgraded and have just been installing the updates as they come to me. 

does anyone know why this might be? it is a relatively new drive so i cant see it being that as the problem, and the dvd i`m trying to read is practically brand new, no scratches etc

any help would be appreciated as always

here`s my fstab, if there is anything else you might need to help solve the problem just let me know


Thanks


DK


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by DiscoKiller on 2006-10-11
ok so i booted up with a disk in the drive and now it seems like it wants to work

sweet....i guess...


Peace

DK

---

