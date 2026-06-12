---
title: "CD-R/W and DVD never mounted"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-18
Is there a "model" fstab that shows what a working system would look like? 

mark@Lexington:~$ dmesg | tail
[   78.801292] Bluetooth: L2CAP socket layer initialized
[   78.811609] Bluetooth: RFCOMM socket layer initialized
[   78.811641] Bluetooth: RFCOMM TTY layer initialized
[   78.811648] Bluetooth: RFCOMM ver 1.8
[   83.845417] NET: Registered protocol family 10
[   83.845731] lo: Disabled Privacy Extensions
[   94.516234] ath0: no IPv6 routers present
[  118.130560] ath0: no IPv6 routers present
[ 5673.903154] sr1: disc change detected.
[ 5709.915199] sr1: disc change detected.
mark@Lexington:~$ 

The last 2 lines of dmesg come from calling "mount" from Places/Computer and right clicking the dvd icon.

/etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9dea8cc1-82db-49a6-85fe-cf8d41d5f398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=82ad16ec-a20d-406e-ba15-becd1f1e6342 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,unhide,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,unhide,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb1 /mnt/Drive2	ext3	defaults	0	2
#above line added by mp on july 25, 2007
# additional ,unhide, added to /dev/scd0 and scd1 by mp 8/18/07

are tabs and spaces critical in this file? 

The 2 optical drives will work with Feisty Live-CD. What gives here?

---

### Post by Happy_Man on 2007-08-18
I'm just taking a shot in the dark here, but what if you deleted the word unhide from both the CD entries in fstab? Back it up first, in case something weirder happens.

---

### Post by Mark_in_Hollywood on 2007-08-18
I had added the ,unhide, less than 1 hour ago, following advice & instruction at another post. The DVD does not mount or work with or without the ,unhide,

I also ran Feisty Live-CD and the DVD can't mount there either.

Any other ideas?

---

### Post by Mark_in_Hollywood on 2007-08-18
OK, I've removed the ,unhide, from the /etc/fstab

which now reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9dea8cc1-82db-49a6-85fe-cf8d41d5f398 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=82ad16ec-a20d-406e-ba15-becd1f1e6342 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb1 /mnt/Drive2	ext3	defaults	0	2

also:

Trying to mount what Places/Computer calls CD-ROM 2 returned:

mount: special device /dev/scd1 does not exist

---

