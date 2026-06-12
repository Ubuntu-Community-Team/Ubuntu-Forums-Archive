---
title: "[SOLVED] uninstall ubuntu"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-12-29
i already fixed the MBR now i need to erase the partition... how can i do that?? i dont want my winows partition damaged.

---

### Post by taurus on 2007-12-29
Boot with Ubuntu LiveCD and use gparted in System -> Administration to erase those Ubuntu partitions.

---

### Post by overdrank on 2007-12-29
> **patchido said:**
> i already fixed the MBR now i need to erase the partition... how can i do that?? i dont want my winows partition damaged.

HI and this link will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck!
Edit to slow again lol :)

---

### Post by meindian523 on 2007-12-29
or simply:

Right click My Computer>>Disk Management

Delete those partitions which Windows doesn't recognize,that is the ones without labels like C:,D:,etc and those whose filesystem field is blank,and Ubuntu is gone from your system,provided you didn't install any other OS

---

### Post by FuturePilot on 2007-12-29
You could do it from the Ubuntu live CD and use GParted or download the GParted live CD.
[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")
I would recommend the GParted live CD but either way, run GParted and delete the Linux EXT3 partition and the Swap partition and then the empty Extended partition. Then just resize your Windows partition to take up the whole drive.

---

### Post by zipperback on 2007-12-29
> **patchido said:**
> i already fixed the MBR now i need to erase the partition... how can i do that?? i dont want my winows partition damaged.


Boot your Ubuntu LiveCD and then from the desktop, use gparted to delete the partition in question.

zipperback
:popcorn:

---

