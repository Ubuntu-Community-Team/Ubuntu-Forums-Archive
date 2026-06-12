---
title: "Can I view Win XP file systems on Ubuntu?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Ederico on 2007-02-25
Hello,

Is it possible to view Windows file systems on Ubuntu 6.10 (I have a dual boot Win XP Pro + Ubuntu CE 2.0 system)?

Unfortunately I cannot seem to be able to view the Windows file systems through Ubuntu, but I could using SUSE Linux 10.1. Is there a way to change this?

Thanks beforehand for any assistance.

Ederico.

---

### Post by haricharan on 2007-02-25
yes u can..u have to modify /etc/fstab file...just copy paste the contents of /etc/fstab file here
```
cat /etc/fstab
``` lets see if you have mounted the filesystems properly....

---

### Post by OrTigaS on 2007-02-25
HI! just my 2 cents. here: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) 

it will help you a lot not only view but read and write :)

---

### Post by Ederico on 2007-02-25
> **haricharan said:**
> yes u can..u have to modify /etc/fstab file...just copy paste the contents of /etc/fstab file here
```
cat /etc/fstab
``` lets see if you have mounted the filesystems properly....

In reply to you:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a724e080-1824-414b-b6c1-acf1df34d36e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=88463619-691c-47f2-a45f-8d66714c813e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Ederico on 2007-02-25
I managed using the instructions featured in the thread linked by Ortigas. Thanks and cheers. :)

P.S. Seems to work fine, pretty straightforward as well.

---

