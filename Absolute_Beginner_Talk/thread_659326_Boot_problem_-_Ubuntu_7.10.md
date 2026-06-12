---
title: "Boot problem - Ubuntu 7.10"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Cold-Gin on 2008-01-05
Hi. I have read a couple of other posts regarding long boot times, but my symptom is a little bit different. After I choose Ubuntu from the dual boot menu, I get a black screen for about 2 - 3 minutes. Then, finally the familiar tan screen appears after the long delay, and I get the login prompt. Everything is fine after that.

Perhaps this is a hardware issue or something, but I am not sure. I had a similar (but not exactly the same) problem with 7.04, and this fixed it:

[http://ubuntuforums.org/showthread.php?t=487227](http://ubuntuforums.org/showthread.php?t=487227)

The booting delay on the black screen only reappeared after upgrading to 7.10. The boot time was very fast after I made the modifications in the link above for version 7.04.

Current version: Ubuntu 7.10

My PC:

Gateway 300X
Celeron 1.8GHz processor
768MB ram

Thanks.

---

### Post by dstew on 2008-01-05
Quick guess -- the bootup delay is due to the IPv6 module. See [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841) or [http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html](http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html)

---

### Post by SOULRiDER on 2008-01-05
When you are going to select a kernel to boot press **e** and delete splash and quiet, then press **b** to boot.
Try to see if you get any errors and tell us how it goes.

---

### Post by SOULRiDER on 2008-01-05
> **dstew said:**
> Quick guess -- the bootup delay is due to the IPv6 module. See [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

Thats good to know, thanks for answering.

---

### Post by Cold-Gin on 2008-01-19
I'm so sorry for not replying sooner...

SOULRIDER - Thank you. Your suggestion to edit the boot option does work (I only had a chance to try it for the first time today, as I hadn't had time to work with this machine until now)

The only thing is, I tried to follow the instructions in the link that I mentioned in my original post to make the modifications permanent, but that does not seem to work.

In my /boot/grub/menu.lst file, on the kopt= line, I do not have quiet and splash specified (I had removed those options during my 7.04 installation, and the settings were retained when I upgraded to 7.10), yet those options appear each time I boot and choose option e (on the black configuration screen under kernel). I have to manually remove them on each boot.

Is there some other file or option that I can change to remove quiet and splash from the boot loader?

Thank you!

---

