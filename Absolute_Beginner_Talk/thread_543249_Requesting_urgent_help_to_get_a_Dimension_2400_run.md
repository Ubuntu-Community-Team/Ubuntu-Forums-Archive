---
title: "Requesting urgent help to get a Dimension 2400 running."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-09-04
Hi,
   I don't intend to rush anyone, but I have tried to get Feisty installed on this computer properly for about a month now. I finally have it running, but it has many errors and the owner of this computer needs it running ASAP.

-Boots without a splash screen (It has done this through 2 installs and through the Live CDs)
-Can connect to a wired network but wireless can not connect due to the fact that it shows all of the         connections at zero percent. I am using a Linksys usb adapter that I never had to configure on other computers (using the very same adapter)
-When following the "Enable multimedia" guide on this forum, the computer freezes while installing Java. I was not able to complete the guide
-Computer also runs slow and glitchy, many programs have to be forced closed, many programs just do not work.

It is a Dell Dimension 2400
256MB RAM
20GB Partition
Feisty with latest basic updates (No extra sources, only the ones activated with Ubuntu)
Pentium 4 processor

Any help would be great. Thank you very much for your time.

---

### Post by nowshining on 2007-09-05
-Boots without a splash screen (It has done this through 2 installs and through the Live CDs)
 
A =  that is minimal - as long as it enters the gui program area it's fine, maybe somehow it got turned off :/ - small problem...
 
-Can connect to a wired network but wireless can not connect due to the fact that it shows all of the connections at zero percent. I am using a Linksys usb adapter that I never had to configure on other computers (using the very same adapter)
 
A = have to wait - But maybe you need to download the right drivers somewhere - or set WPA up and such..
 
 
-When following the "Enable multimedia" guide on this forum, the computer freezes while installing Java. I was not able to complete the guide
 
A= what version
 
-Computer also runs slow and glitchy, many programs have to be forced closed, many programs just do not work
 
A= give some examples....






edit: oh most likely wait a month until Gutsy and it might fix your problems... :/

---

### Post by kevindubrow on 2007-09-05
I am pretty sure it is Java 6 (I will know for certain in a few hours). It freezes when the time comes to check the "Accept to license" box. You are also not able to scroll through the license.

Programs that don't work: 
-Any audio program trying to play a CD. I made sure the CDs were not mp3 CDs when playing them also because I do not have the multimedia enabled. The programs will recognize the CD and even find track names, but will not play. Ripping to a library and trying to play the files will also result in a freeze.

The computer runs slow in every process.

The computer also will stop functioning after a period of time:
-Can not access the shutdown menu.
-All programs have to be forced closed.
-Keyboard will stop typing for a short amount of time.

And to throw another hammer into this; the failed install of Java is creating issues. I had to run the dkpg command to get the package manager running (I used the command it told me to use). Once I was in the package manager, I found the two broken Java files and marked them for removal. The removal failed and I was told that a reinstall would be safer. When reinstalling, it will freeze at the same point.

Thanks very much.

---

### Post by afonic on 2007-09-05
Sounds to me like some piece of your hardware has problems with Linux, maybe the mobo.

Have you looked into the details for your hardware? Have you tried another Linux distro?

---

### Post by bks on 2007-09-05
How does it run in Live CD mode?  I know my computer ran fine with the Live CD, but when I installed it, hardly anything worked.  It turned out to be driver issues and was fairly simple to iron out.

---

### Post by kevindubrow on 2007-09-05
Hardware:

Processor: Intel Pentium 4
Chipset: Intel 845GV chipset
Videocard: Integrated Intel Extreme graphics
Sound: Integrated Soundmax Sound
Memory: 256MB PC-2700 DDR memory (one module)
Networking: Integrated 10/100 Ethernet
Hard Drive: Seagate Barracuda 40GB ATA/100 7200RPM hard drive
CDROM: 	Hitachi 48X CD-ROM drive
CDRW
PCI 56K modem

Are any of those specifications incompatible? And no, I haven't tried another distro.

The computer ran horribly in the LIve CD mode. No splash screen and it took about an hour just to get Ubuntu installing on the computer...longer than it took to install. I ended up reinstalling with an Alternate CD in text mode.

Many thanks.

---

### Post by mlentink on 2007-09-05
Is it at all possible to add memory? Ubuntu&#347; minimum spec is about 192 Megs. Yours has 256, but I bet you can subtract around 64Meg Video (Shared!) from that. I think it'll run fine with 512.

---

### Post by oilchangeguy on 2007-09-05
> **kevindubrow said:**
> Hardware:

Processor: Intel Pentium 4
Chipset: Intel 845GV chipset
Videocard: Integrated Intel Extreme graphics
Sound: Integrated Soundmax Sound
Memory: 256MB PC-2700 DDR memory (one module)
Networking: Integrated 10/100 Ethernet
Hard Drive: Seagate Barracuda 40GB ATA/100 7200RPM hard drive
CDROM: 	Hitachi 48X CD-ROM drive
CDRW
PCI 56K modem

Are any of those specifications incompatible? And no, I haven't tried another distro.

The computer ran horribly in the LIve CD mode. No splash screen and it took about an hour just to get Ubuntu installing on the computer...longer than it took to install. I ended up reinstalling with an Alternate CD in text mode.

Many thanks.

if you've only got 256mb of ram. and onboard video, there's your porblem. not enough ram. the computer needs at least 256mb of ram, and the video is taking some of that. unless you can upgrade the ram, you'll need to use a lighter version. such as xubuntu.

---

### Post by kevindubrow on 2007-09-05
Wow, thats really going to bum the owner of the computer out. Are we sure these problems are related to the RAM? Most issues seem like ram isn't the issue. On top of that, I have Song Bird, Firefox, Thunderbird, and Gaim open right now and I am only using 248.8 MB of RAM. The video card on this computer isn't on board, but shouldn't Ubuntu be able to run with 256mb considering that my friend will not have that many programs open? I know Ubuntu can have issues out of box (I have experienced many with other computers), but they were all able to be fixed.

Sorry to be so pushy...but is RAM definitely the issue here? Thank you.

---

### Post by afonic on 2007-09-05
Maybe you can download Xubuntu and see how it does.

If you problems are disappeared, it seems like RAM was the culprit.

---

### Post by kevindubrow on 2007-09-05
Ok, I'll get Xbuntu installed. Thanks so much for your help everyone. Very fast; this community is amazing!

---

