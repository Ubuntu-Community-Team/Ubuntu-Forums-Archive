---
title: "Gutsy - cdrom problem, can someone tell me what there fstab entries should look like?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-11-04
gutsy upgrade left them as /dev/hdc and /dev/hdd but I know this is not right.

---

### Post by forestpixie on 2007-11-04
hey ho - this is what mine looks like if that's a help

> kevin@kevin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2db5fad-2540-4c3a-ac21-bd124059a495 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=dabb09c2-964c-466d-a039-cde4c30d23f8 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=eebef378-1b5c-4b93-8d8c-8fa430f2dc73 /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=6cebc2cf-6ba9-4c38-bdd8-5abf91ebf7d3 /media/sdb2     ext3    defaults        0       2
# /dev/sda3
UUID=8150326b-3b03-4e2a-bc5b-e0335617f2cf none            swap    sw              0       0
[COLOR="Red"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0[/COLOR]

---

### Post by philinux on 2007-11-04
Ok changed fstab to sdc0 and sdc1.

Sound juicer can play an audio disk so can rythmbox but not totem or realpayer.

---

### Post by forestpixie on 2007-11-04
well that's a bit odd I'd say - I don't actually use my cd for playing audio very often, checked an dit works ok for me.

Don't know if there's anywhere that you can specify cd for totem or realplayer

Sorry I can't be of more help, the only thing I'd try would be to reinstall

---

### Post by tjk on 2007-11-04
Don't know if I'm having exactly the same issues, but both my cdrom and dvd/cdrom are not reading audio cds.  So if anyone knows of a solution, I'd like to know it too.

The weird thing is, that I was able to rip and audio CD a couple of days ago (long after I upraded to Gutsy).

Running Kubuntu Gutsy - 64bit.

---

