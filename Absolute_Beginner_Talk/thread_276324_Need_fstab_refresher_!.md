---
title: "Need fstab refresher !"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-10-12
Ok,got this: So........guess I'll have to make a directory and mount it in
fstab.. it's a dvd-recorder,same properties as the cd recorder or ?? Her's my fstab now. Thanks ! :) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto,exec    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /Foghorn        ext3    rw,user,auto,exec    0       0

---

### Post by 5-HT on 2006-10-12
Yup, using the same properties (albeit with the proper device name and mount point) as for the CD recorder should be fine: it's what Ubuntu automatically used for my fstab on install.

---

### Post by Drakkor on 2006-10-12
Yep,thanks,got the fstab,but it still wanted root privileges so... I went
gksudo k3b and finally was able to make it, why would I need root to burn 
a dvd ??? :-k

---

