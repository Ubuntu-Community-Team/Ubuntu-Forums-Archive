---
title: "Grub will not boot Dapper"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2007-02-27
I just reinstalled Dapper- it all went well but when it came time to boot grub gets to 1.5 and then error 18.

The history is:
I was running edgy and ruined my ext3 partition, spent a day trying to get it back and when I was sure it was gone I reinstalled Dapper. I let the install CD do the partitioning.

I have XP on a seperate HDD which is running secondary to my Ubuntu HDD. This has worked for me through many Ubuntu installations. I cannot understand why grub did not load properly.

Need help again. I have the 6.06 live CD and the gparted live CD.

---

### Post by wireddad on 2007-02-27
**Error 18** : **"Invalid or unsupported executable format"** This error is returned if the kernel image boing loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).



[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)



Something must have happened during the re-install.   Have you tried reloading Dapper?  Really not sure.  :confused:

---

### Post by kindafunnylookin on 2007-02-27
I'll try a reinstall right now

---

### Post by kindafunnylookin on 2007-02-27
Well, the reinstall worked. Thanks for bringing it up.

---

### Post by wireddad on 2007-02-27
Awesome.

---

