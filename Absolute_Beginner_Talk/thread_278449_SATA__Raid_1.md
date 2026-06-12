---
title: "SATA  Raid 1"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by netengit on 2006-10-16
Hi guys,

I have two identical 120gig discs in my machine using raid 1 (mirrored)

However ubuntu only seems to recognise them as 80gig drives any ideas???

root@vmserver:/tmp# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73774880    883844  69143476   2% /
varrun                 1558196        44   1558152   1% /var/run
varlock                1558196         4   1558192   1% /var/lock
udev                   1558196       104   1558092   1% /dev
devshm                 1558196         0   1558196   0% /dev/shm

I was runnning fedora and they were seen correctly??

Cheers

Scott

---

### Post by netengit on 2006-10-16
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Just incase usefull

---

### Post by netengit on 2006-10-18
Anyone???;)

---

