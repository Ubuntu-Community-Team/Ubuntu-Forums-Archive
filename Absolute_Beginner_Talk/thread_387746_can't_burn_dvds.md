---
title: "can't burn dvds"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by wildkarde on 2007-03-18
Out of nowhere, i can't burn dvds anymore.  In fact, DVD aren't even being autodetected.
CDs are working fine tho.

$growisofs -speed=2 -dvd-compat -Z /dev/hdc=ufc51-dvd1.iso
:-( /dev/hdc: media is not recognized as recordable DVD: 0

dmesg | grep DVD
[17179578.932000] hdc: _NEC DVD_RW ND-3550A, ATAPI CD/DVD-ROM drive
[17179579.716000] hdd: SONY DVD-ROM DDU1615, ATAPI CD/DVD-ROM drive
[17179579.788000]  hda:<6>hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.792000] hdd: ATAPI 40X DVD-ROM drive, 1725kB Cache, UDMA(66)

I installed both gnomebaker and k3b and both fail to burn the dvd.  It was working before.  

Thanks in advance.

---

### Post by bruenig on 2007-03-18
Paste the contents of /etc/fstab.

---

### Post by wildkarde on 2007-03-21
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=4154794c-ff7b-4618-8376-fbe6f11a9209 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=D4A85758A8573866 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=45DE-26B7  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=afc3313e-0b2d-49db-a409-9cd23ffa11cd /media/hdb5     ext3    defaults        0       2
# /dev/hda5
UUID=0f5d8d9c-2d21-4283-983f-53d095b16f18 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

