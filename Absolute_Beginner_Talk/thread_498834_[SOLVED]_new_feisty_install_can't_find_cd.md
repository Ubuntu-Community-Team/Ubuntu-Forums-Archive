---
title: "[SOLVED] new feisty install can't find cd"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-11
This laptop has had feisty installed.

It has had nothing modified WHATSOEVER.

It has had a few files put on the desktop, OO-Writer's icon put on the panel along with terminal and text-editor icons. 

THAT'S IT.

Why on earth can't the laptop now find the very cd (canonical's feisty install cd) that installed it???!!!

Why does the Places/Computer/CD-RW-DVD-ROM return a unmounted "state"?

NUTS!

---

### Post by bren on 2007-07-11
ok just guessing here....coz its not clear from what you said

possibility 1) you previously did install ubuntu but have accidentally booted from CD this time.....thats why CD is unavailable its locked coz it is a LIVE CD boot

possibility 2) you have a cdrom mount problem

post /etc/fstab here

---

### Post by Mark_in_Hollywood on 2007-07-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=008ba7da-bfbb-413a-b9c8-ef20243748b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cd7caa86-3cb0-4fd1-b51b-b083b9b3bd9c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Mark_in_Hollywood on 2007-07-24
After a lot of coughing, and using a Gutsy desktop cd, too, the laptop Toshiba Satellite 1905-s304 is working.

---

