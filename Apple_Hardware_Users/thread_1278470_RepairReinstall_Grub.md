---
title: "Repair/Reinstall Grub"
date: 2009-09-29
forum: Apple Hardware Users
---

### Post by somethingkindawierd on 2009-09-29
I have a dual-boot setup on a [Macbook2-1]("https://help.ubuntu.com/community/MacBook2-1/Jaunty") running OS X 10.5 & Ubuntu 9.04, and booting with rEFIt. I recently thought to try Ubuntu 9.10 alpha, so I booted from the live CD and installed it onto a USB drive (I never told the installer to touch my other drives.)

But, sadly, it messed up my grub. I can boot into OS X fine, and rEFIt shows the Ubuntu partition, but when it goes to boot Ubuntu I see a black screen showing only this:

```
GRUB 
```How can I fix my grub? I have a 9.04 live cd...is there a way with that?

---

### Post by rjcalifornia on 2009-09-29
I would like to know that too... Also, is it possible to change the GRUB Screen to something that looks... nicer?

---

### Post by lrcaballero on 2009-09-29
Try watching this video on youtube, installing GRUB!!!!!
Good luck!!!!


[http://www.youtube.com/watch?v=WtBBl6HvdpM&feature=related](http://www.youtube.com/watch?v=WtBBl6HvdpM&feature=related)

---

### Post by somethingkindawierd on 2009-09-30
The [instructions here for reinstalling grub]("http://ubuntuforums.org/showthread.php?t=224351") worked perfectly. I followed the second set of instructions below the edit. (the video linked above by lrcaballero covered the 1st method which did not work for my problem.)

The second set of instructions at the link above involves booting into the live cd, performing a few terminal commands to fool grub into working on your hard drive (NOT the live cd) filesystem, and then reinstalling grub.

---

