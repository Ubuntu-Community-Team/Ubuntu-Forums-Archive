---
title: "Xubuntu: Manually selecting Low Resources install?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Starscream112 on 2007-09-10
Hello all!  I'm wondering if there is some way to force the Xubuntu 7.04 alternate install CD into Low Resources mode for a text-only install?



I have a IBM Thinkpad 600e (400mhz PII, 64mb RAM, 10gb HDD) on which I'm trying to install Xubuntu.  I installed 6.06 easily the first time through, but somehow caused the NIC to stop connecting to networks.  I thought my easiest course of action would be to reinstall.

The laptop is nine years old and the motherboard is flaky.  The date and time needs to be input each time it's turned on, the bios memory test reports 128mb RAM, and a few other minor things.  I think the RAM is giving me trouble, though.

When I run the alternate-install CD in text-only install mode, it freezes partway through.  One time when the bios recognized only 64mb RAM the install ran in "Low Resources Mode" (or something like that) and the install would have gone through had power not been lost.  I think the bios tells the installer that I have 128mb RAM, the installer does not run in low resources mode, causing the install to freeze.  

Is there some way that I can force the install to run into Low Resources mode, possibly by using the F6 Advanced Options at the CD boot menu?

Thanks everyone!

---

### Post by wolfen69 on 2007-09-10
see this: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Starscream112 on 2007-09-10
Thank you for the reply.  

I actually came across that page in my searches already, and as a first time linux user, was somewhat intimidated.  I did not want to have to pick and choose window managers and software packages for two reasons.  One, because I would no doubt make unwise choices.  Two, because having anything other than a standard install would make troubleshooting future problems more difficult, as my setup would be slightly different from what any prospective forum answerers would expect, and I might miss out on something important.


To address the first section of your posted link: I was certain my install was not just taking its time.  It would regularly hang, frequently at different stages of the install.  I would leave it for hours to come back to 82%.  Once, when disk thrashing, I let it run overnight thinking it was slowly reading and writing.  I attribute this entirely to the problematic motherboard, but other users may experience these symptoms for other reasons.




In case someone in a similar situation stumbles across this forum thread, I did find something that worked, and allowed me to complete the install as planned: I manually partitioned my disk.  Drive partitioning is rather similar across all OS'es, and the install CD does a great job catching and explaining the linux-specific requirements of the partitions.  I gave myself an 800mb swap partition--space for the install's entire ISO and more besides.  I formatted the rest in EXT3.  

The first time I installed from there, it failed.  The second time completed though, and now I'm playing with my new and once again very useful laptop.  Now, if only I can get the pcmcia wireless nic to work...

---

