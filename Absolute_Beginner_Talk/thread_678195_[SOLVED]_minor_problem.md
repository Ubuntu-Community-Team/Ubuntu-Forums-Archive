---
title: "[SOLVED] minor problem"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Sammael5 on 2008-01-25
I have a 500 gb Western Digital xternal HD.  it wont mount.... suggestions?

---

### Post by Origin415 on 2008-01-25
What error messages do you get?

---

### Post by skymera on 2008-01-25
can yoy post the outputs of

```
sudo fdisk -l 
```

and 

```
 cat /etc/fstab 
```

---

### Post by Sammael5 on 2008-01-25
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dbac1ae2-8411-483a-a37c-906c29b8a4b3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=a374a90c-03da-467a-a01d-74b30d42c312 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

helpful?

---

### Post by skymera on 2008-01-25
seems your disk isnt in fstab, we can add that. Personally i sdont know how.

and did i post the second command wrong its a lower case L.

```
 sudo fdisk -l 
```

---

### Post by Sammael5 on 2008-01-25
looked like a one
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18748   150593278+  83  Linux
/dev/hda2           18749       19457     5695042+   5  Extended
/dev/hda5           18749       19457     5695011   82  Linux swap / Solaris

---

### Post by skymera on 2008-01-25
yeah it does, sorry should have noted.

Do you have your disk plugged in and turned on?

sorry im not much use, never really done this myself :wink:

hope someone else can guide you in the right direction

---

### Post by Sammael5 on 2008-01-25
it is plugged in and turned on... but nothing else is happening

where should i go to get someone with more knowledge?

---

### Post by skymera on 2008-01-25
think waiting would be a good idea.

hopefully someone should get back to you :)

in the mean time you could browse the other threads :wink:

real sorry i couldnt be more help

---

### Post by Sammael5 on 2008-01-25
no worries man.. just re posted on general help

---

### Post by Jelmoh on 2008-01-25
The best thing to do is google for your answer (Did the dirty work for you this time.. :P)
[Solution #1](http://ubuntuforums.org/archive/index.php/t-150412.html)
[Solution #2](http://www.mydigitallife.info/2006/09/10/how-to-mount-usb-disk-drive-in-unix-or-linux/)
[Solution #3](http://www.linuxforums.org/forum/linux-newbie/69019-how-mount-usb-drive.html)

All are quite the same but just a little different explanation...
The last is quite simple, but with the three combined you should get it to work.. :)

Good luck! :D

---

