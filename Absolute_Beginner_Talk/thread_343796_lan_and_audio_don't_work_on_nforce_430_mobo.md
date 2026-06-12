---
title: "lan and audio don't work on nforce 430 mobo"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by supremejosh on 2007-01-22
Hi, I have tried installing 6.10 64bit ubuntu, and I can't get lan or audio working (lan is most important because then it saves me rebooting into windows every time for help).

I have a 6100 / nforce 430 am2 motherboard. I also have a 7600gs that I haven't even bothered trying to get going yet.

I don't think that anything is detected properly, if I go lspci almost everything shows 'unknown' (or something like that anyway).

I have been googling and looking around but I haven't found anything overly helpful yet. nVidia apparently has nforce drivers but none of them seem to install or have the right files. It also doesn't help that I am n00b at linux and don't really know exactly what to look for anyway.

Also, is it really worth having the 64bit version? If it is going to be more complicated for little to none performance boost then I might download and install 32bit...

---

### Post by supremejosh on 2007-01-22
Would something like this do it?

[http://drivers.softpedia.com/get/GRAPHICS-BOARD/NVIDIA/nVidia-Linux-nForce-Driver-AMD64EM64T-10-0310.shtml](http://drivers.softpedia.com/get/GRAPHICS-BOARD/NVIDIA/nVidia-Linux-nForce-Driver-AMD64EM64T-10-0310.shtml)


The last one I tried said that I needed something I didn't have, and I will go and get it if it will fix the problem...

---

### Post by kvonb on 2007-01-22
Mate I would ditch the 64bit version right now to save yourself some MAJOR headaches!

There are a lot of problems that don't get worked on as quickly as the standard version.

As for your network, have a look on the mainboard and see if you can find the chip type, or easier look in the manual then search these forums for answers.

Is it by chance an ASUS board?  If so, the Linux lan drivers should be on the driver CD that came with it.  Some of the chips they use are not supported as of yet, but their drivers do work (so I've heard!).

As for sound, same again, find out what chip is used and do a search on these forums for that, it should turn up results.

Your video card is the easiest thing of all, just download the latest version of the driver from [www.nvidia.com](www.nvidia.com) (the Linux one obviously!) and follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Scroll down the page and use _**ONLY**_ Step2, Option2, which installs the driver that you downloaded.  If you feel adventurous you can then go on to install Beryl at a later date.  Beryl is NOT for beginners though, so just leave it for now, plus it has a few problems with the latest release :).

Regards, KEv :)

---

### Post by supremejosh on 2007-01-22
Thanks! The replies are quick around here :)

I'm going to take your advice and pop around to my friends house to get a 32bit cd. I'll try the rest of it after that.

O, and it is a gigabyte motherboard.

---

### Post by supremejosh on 2007-01-23
Ok well I can't get it working yet, although I found a thread:

[http://ubuntuforums.org/showthread.php?p=1989114](http://ubuntuforums.org/showthread.php?p=1989114)
Nvidia nforce 430, network problems and kernel 2.6.19 - Ubuntu Forums

About my problem, and they are solving it by updating to a newer kernel (2.6.18+, ubuntu comes with 2.6.17 I think?). Problem is that it is going to be a pain trying to do this without internet (to get packages etc).

Any ideas anyone? If I can't get this going after a while I might just try a different distro with a later kernel :(

---

### Post by spafbnerf on 2007-02-01
the nforce onboard lan+sound on the mobo i bought for my gf'z grandad, a GA-M61VME-S2, isn't recognised under dapper or opensuse 10.2. :(

most upsetting ... :(

---

### Post by spafbnerf on 2007-02-03
try the new feisty fawn beta it should work.. i got this hardware working on opensuse 10.2 by installing a kernel 2.6.20 rpm from the unstable version...

---

