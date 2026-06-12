---
title: "Experts Please read need your help (urgent)"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-08-12
good day to all.... i have a problem on my cd rw drive... i cant burn anytihng on it... these are the deatails....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda1       /windows2       ntfs    nls=utf8,umask=0222 0   0
/dev/hdd1       /windows        ntfs    nls=utf8,umask=0222 0   0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Then....when i insert a blank Cd-R the error pops up:.....


Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
deatails:
mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so


please help me out i have things due on 2 hours and i need my rom.... please please please :(

---

### Post by rck_hitokiri on 2006-08-12
Some more info's:



[ 3812.369029] attempt to access beyond end of device
[ 3812.369619] hdc: rw=0, want=68, limit=4
[ 3812.370001] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[ 3812.480127] cdrom: This disc doesn't have any tracks I recognize!
[ 4030.568508] cdrom: hdc: mrw address space DMA selected
[ 4030.597184] cdrom: hdc: mrw address space DMA selected
[ 4030.645946] attempt to access beyond end of device
[ 4030.646562] hdc: rw=0, want=68, limit=4
[ 4030.647067] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[ 4030.749665] cdrom: This disc doesn't have any tracks I recognize!


:((

---

### Post by [S|G] on 2006-08-12
What program are you using to try to burn the cd with?

---

### Post by rck_hitokiri on 2006-08-12
I tried the default write to cd/dvd and gnome baker.... nothing worked... any help is greatly appreciated. thank you.

---

### Post by sirclaudio on 2006-08-12
It look's like you tried to mount the cd... Or was gnome?

---

### Post by rck_hitokiri on 2006-08-12
i tried to mount it but to no avail i still cant find a way to urn on cd-rs or things like that... im really lost here brothers... please help.... :(

---

