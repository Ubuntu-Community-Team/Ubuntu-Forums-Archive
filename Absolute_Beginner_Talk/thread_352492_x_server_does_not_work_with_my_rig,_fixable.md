---
title: "x server does not work with my rig, fixable?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-03
I finally got ubuntu 6.06 installed in safe graphics mode. All other modes won't work and none of the newer versions will work either. 6.10 will start loading but then a line of green and blue appear on the screen and everything just freezes. So I got 6.06 to work, but when I tried to update the video settings using x server if fails to start now. Does this mean that with my hardware I won't be able to use any accelerated graphics? Or do I need specific drivers to make it work? Also, I didn't use the amd64 version to install, but I was told that i didn't need the 64 bit version. was this a mistake? should I have used the 64 bit version?

My hardware specs:
My hardware setup:
ATI RADEON X850 XT 256MB 16X PCI EXPRESS
(939-pin) AMD ATHLON64 FX 55 CPU w/ Hyper Transport Technology
(939-pin Socket) ASUS A8V-E Deluxe VIA K8T890 Mainboard
2048 MB (1GBx2) PC3200 400MHz Dual Channel DDR MEMORY Corsair XMS High Performance Memory w/ Heat Spreader
Western Digital Raptor 74GB 10,000RPM Serial ATA 150 8MB Cache WD740GD
ULTRA X-Connect 500W ATX PS w/2 80mm Fans
Memorex 52x CDRW/DVDrom

Also, since I installed 6.06 after 6.10 I have this weird situation:
i managed to go through the manual partitioning of the 6.06 version. It worked! ubuntu 6.06 seems to be working, but the 6.10 version is not. 
When the boot menu comes up, it has 5 options for ubuntu instead of the first three that i first saw. Now there's:

Ubuntu, kernel 2.6.15.27-27-386
Ubuntu, kernel 2.6.15.27-27-386 (recovery mode)
Ubuntu, kernel 2.6.15.27-26-386
Ubuntu, kernel 2.6.15.27-26-386 (recovery mode)
Ubuntu, memtest86+

and then Windows XP

Now either of those Ubuntu choices seem to do the same thing, but it's weird that there are so many options isn't there?

---

### Post by riven0 on 2007-02-03
The 64bit version will only give you a faster speed at the cost of program compatibility. If you're willing to work out the numerous problems with flash, then go for it, otherwise stick with 32bit. You'll be happier. 

In either case, you'll still have to install the ATI drivers. When you boot up, and you get to the garbled screen, can you hit CTRL + ALT + F1 to get to the terminal? If you can't, then just try these commands one at a time in the recovery mode:

> sudo apt-get update 

> sudo apt-get install xorg-driver-fglrx

> sudo apt-get install fglrx-control

> sudo depmod -a

> sudo aticonfig --initial 

> sudo aticonfig --overlay-type=Xv

Then reboot and see if that helps at all.

---

