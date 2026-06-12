---
title: "USB Drive and Fiesty"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-07-03
I have a unique problem (I think).

I have three computers running fiesty two of them will recognize my USB "pin" drive.  One won't.  On the machine that doesn't automount it will show up in the Computer "Places".   But, when I try to double-click (or select Mount) to mount it will say the drive can not be mounted, "Probably media is missing".  Other USB devices like Mice, Keyboards, and USB HardDrives work fine.

What is wrong?

---

### Post by nitro_n2o on 2007-07-03
do you have the /media directory in your file system 
maybe your hardware is malfunctioning

---

### Post by weaver4 on 2007-07-03
Yes I have the media directory.

I have dual boot and when using WinXP with the same hardware it reads the USB device correctly.

This use to work with 6.10.

---

### Post by weaver4 on 2007-07-03
In the system log file I get these messages over and over.

Jul  3 18:03:11 trey-ubuntu kernel: [  381.294935] sda : READ CAPACITY failed.
Jul  3 18:02:51 trey-ubuntu kernel: [  361.301899] sda : status=0, message=00, host=1, driver=00 
Jul  3 18:02:23 trey-ubuntu kernel: [  333.293003] sda : sense not available. 
Jul  3 18:00:55 trey-ubuntu kernel: [  245.395053] sda: Write Protect is off

Again the usb drive works fine in my other ubuntu systems, and works on this system when I boot into Windows.

What else should I look at?

---

