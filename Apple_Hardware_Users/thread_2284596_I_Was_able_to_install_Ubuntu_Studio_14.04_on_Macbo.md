---
title: "I Was able to install Ubuntu Studio 14.04 on Macbook Pro 4.1"
date: 2015-06-30
forum: Apple Hardware Users
---

### Post by Tux4Prez on 2015-06-30
I am posting this thread because I cannot seem to find any documentation on installing UbuntuStudio 14.04 on a macbook 4.1 (early 2008). I have been able to do it however with some catches. In the interest of full disclosure, I have a dead battery on my MBP so I'm not sure if the first catch is necessary in all cases.

1. I have to use the acpi=off parameter for a successful boot (in both LiveDVD and in GRUB. Also, I can't remember if I needed nomodeset on liveDVD or not)
2. I use rEFInd for my boot loader. I tried using the bless command I have read so much about but was dissatisfied with its results and would only boot os x in low resolution mode, so I do not recommend it.
3. I cannot seem to get my airport wifi adapter working in ubuntu. It works in os x and is a broadcom 4321 chipset. Tried using the broadcom STA driver, b43-fwcutter, and bcmwl drivers but all to no avail. USB dongle works, however so I can live with that for now.
4. I do not get any keyboard backlighting (I'm interested in addressing this problem)
5. I have not tested the iSight camera, as I'm not very interested in that anyways
6. I have not tried the function keys except for the volume keys (f10, f11, f12) which all work
7. I do not have dimming control for my monitor backlight. That doesn't concern me very much at this time though
8. Sometimes I lose my default theme and have to clear my ~/.config/xfce4/xfconf/xfce-perchannel-xml/ directory to get it back and have to reconfigure any desktop and folder options, like single-click and all that.

Those are the only things I can think of that there may be issues with at this moment. All else seems to be working ok. I get sound and can play video. Most, if not all software I've tried seems to work.
I posted this to let people know that it is doable to install Ubuntu Studio Trusty on a macbook pro 4.1. I have not been able to find anything in the mactel and mactel-support PPAs for Ubuntu Trusty. I welcome advice from anybody who wishes to help address the above issues.



update: Upon replacing dead battery with new one, I no longer need the "acpi=off" parameter, as I figured would be the case. With that, I gained the use of both cores, software shutdown, and monitor backlight dimming, but I am still having dificulty with the keyboard backlight. Apparently the built-in wireless adapter must have something to do with acpi, as it too is now working with the b43 module. A working battery seems to do a lot more than I ever guessed for these computers.

---

### Post by Tux4Prez on 2015-07-15
I started this thread because, while there is no documentation for installing Ubuntu 14.04 on a Macbook 4.1, it is definitely possible. Most of the above issues I was having have been resolved by installing a new battery, as I suspected some would be. A lot of installation guides for installing Ubuntu on Apple hardware suggest using the bless command, however, I do not. I have a dual-boot configuration and get satisfactory results using rEFInd. As mentioned above, I attempted to bless my ubuntu partition and ended up with undesirable results, namely os x's performance was painfully slow and would only appear in low (640x480?) resolution. Attempts to reverse bless failed, and I was only able to undo it by clearing my NVRAM/PRAM then reinstalling rEFInd from os x. I am happy to report that everything seems to be working on my Ubuntu install (including iSight, which I have now blacklisted by default for privacy reasons. A simple modprobe uvcvideo can turn it on when/if I want it.). The best advice I can give here is to make sure you have a good battery installed if you do not want too many performance problems. Even with those problems, however, Ubuntu Studio still performs faster than OS X Leopard. :D

---

