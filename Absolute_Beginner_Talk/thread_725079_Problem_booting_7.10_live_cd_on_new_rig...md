---
title: "Problem booting 7.10 live cd on new rig.."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by makko on 2008-03-15
Hi,

I have tried booting from a live cd that I know works on a new machine I have just built.

Here is a breakdown of what is happening:

From main boot menu I select : Start or Install Ubunutu

after this it goes on to another creen to boot up but I get the following:

busybox v 1.1.3 [some other stuff about debian also]
then a load of errors like these two below:

initramfs [ 120.496661] ata3.00: failed to set xfermode (err_mask=0x40)
[155.766527] ata3.00: failed to set xfermode (err_mask=0x40)

What could be wrong here?
I am trying to boot using a Q6600 and 4GB RAM if it makes things a little easier to understand..

Thanks..

Makko

---

### Post by dstew on 2008-03-15
Othen an error of this type is a hardware problem. Sometimes memory, sometimes a drive problem. Two thoughts. One, the CD may have some marginally visible bits that one CD-ROM drive can see, but another cannot see. Two, there might be some memory issues on the new machine. Try the memory test, and also the CD integrity test.

After that, there might be some kernel parameter options to try.

---

### Post by makko on 2008-03-15
I tried the memory test at one stage and the same thing occured? I will download the alternate cd and also try another distro. gOS because I already have it.. I know it runs on ubunut but it's worth a shot..

---

