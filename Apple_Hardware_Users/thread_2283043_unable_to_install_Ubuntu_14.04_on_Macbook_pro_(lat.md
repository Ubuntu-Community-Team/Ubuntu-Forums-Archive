---
title: "unable to install Ubuntu 14.04 on Macbook pro (late 2013)"
date: 2015-06-18
forum: Apple Hardware Users
---

### Post by birdman2 on 2015-06-18
I want to eventually dual boot my Macbook.  I have tried using the rEFInd boot manager because i thought it would make things simple, but i have not been able to boot into Ubuntu after installation.   I can run a live environment just fine.  There must be some easier way to to dual boot Apple.  Does anybody have any recommendations or experience with these same issues: Correctly partition my drive,  Recommended Ubuntu file format, Boot manager?  Anything helps...  If any more info is needed plz ask

Thanks!

---

### Post by mfox on 2015-06-18
If I recall correctly, the first time you boot after installing Ubuntu as a dual boot, you have to hold down the option key and then choose Ubuntu (or whatever the non-OSX option that appears is called). Once you do that, you will see the rEFind menu thereafter and can choose which OS to boot in.

---

### Post by birdman2 on 2015-06-19
the rEFInd boot manager works fine.  It prompts me to select what OS to boot from, i choose ubuntu and my computer freezes at a purple ubuntu background looking page. Everything installs just fine, i just wonder if i am mounting to the wrong place or if i am using the wrong file format, or maybe if my partitioning scheme is somehow screwing things up

---

### Post by mfox on 2015-06-19
I used the default partition scheme and had no problem with it. However, I installed Ubuntu version 15.04, not 14.04, though I doubt that this would cause you a problem. Also, I installed the default Unity desktop, not some other flavour. One other thing I did was to install with my Mac plugged into an ethernet cable, knowing that the Broadcom drivers are not installed by default and that a bunch of stuff gets downloaded during installation. However, freezing could be related to the video settings at startup, and I can't help you with that because I never tried installing Ubuntu on an Intel MacBook laptop. You could try another desktop, e.g. Ubuntu Mate. Or look into modifying the startup sequence - I know there are threads written on this.

One other thought. The rEFind menu gives me two alternatives; one to the left of the Apple option and the other to the right. The difference has to do with signed and unsigned, and as I recall, the unsigned is on the left. The signed option, which is what I boot from, doesn't suppress the load sequence text. So I don't see the Ubuntu background until I have the log in screen.

---

### Post by davidchute26 on 2015-06-19
It would help if you could post some more information about the partitioning table. To do this in OS X just type "diskutil list" into the terminal or from the Ubuntu live cd/usb "sudo blkid".

---

