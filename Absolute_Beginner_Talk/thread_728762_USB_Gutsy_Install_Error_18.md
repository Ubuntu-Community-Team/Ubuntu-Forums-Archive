---
title: "USB Gutsy Install Error 18"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by spyder99 on 2008-03-19
I recently installed to a USB hard drive. The install went perfect and we used it for weeks. While trying to get my MP3 player to work I made some changes that I didn't like. I figured it would be easier to pop in the live CD and reinstall. I was completely wrong. The install went just as before but upon reboot I always get Error 18. I have tried manually creating partitions with a small partition (100mb) at the beginning; I have tried using the XP format utility (I read that worked somewhere). Nothing seems to work. Why would it work so perfectly the first time, and not work again? Sorry about the long post, but any help would be greatly appreciated. I really do enjoy Ubuntu and want to make the switch.
~shawn

---

### Post by Sef on 2008-03-19
This is GRUB error 18:

> Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Please provide your system specs.

---

### Post by spyder99 on 2008-03-19
Specs:
Athlon XP 2100
Geforce 4200
Soundblaster Live
512mb Ram
USB 20gig Hard drive

Like I said, it worked flawlessly the first time. I have been unable to repeat.
thanks

---

### Post by spyder99 on 2008-03-21
I've tried my HP USB Format Utility but got the same result.

---

