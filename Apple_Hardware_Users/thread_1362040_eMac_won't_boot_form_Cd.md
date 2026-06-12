---
title: "eMac won't boot form Cd"
date: 2009-12-22
forum: Apple Hardware Users
---

### Post by psychovampire85 on 2009-12-22
Okay I have a emac i got from my college teacher. He had put a new hard drive and a cd/dvd drive in it as well as 2 gbs of ram my thing is I want to install ubuntu on it. How do I do it? I have hit and held down the "C" key and it won't go form the cd even with the original Mac discs I have for it.

---

### Post by avtolle on 2009-12-22
Since a new drive was installed, perhaps the firmware should be updated? I run only Ubuntu on my Macs, so I really don't have any experience with the Mac OS, etc., but others will be able to help. Another thought: what is the state of the battery?

---

### Post by psychovampire85 on 2009-12-22
> **avtolle said:**
> Since a new drive was installed, perhaps the firmware should be updated? I run only Ubuntu on my Macs, so I really don't have any experience with the Mac OS, etc., but others will be able to help. Another thought: what is the state of the battery?

He did say I need a new battery for it.

---

### Post by psychovampire85 on 2009-12-23
bump i really need help on this

---

### Post by linuxopjemac on 2009-12-24
if it is a non-Apple hard drive and/or DVD drive you have in there, it might not be supported...

---

### Post by tiresia on 2009-12-24
You can try to reset Resetting PRAM and NVRAM, but I'm afraid that it will be useless.
Anyway to reset PRAM and NVRAM press and hold the Command-Option-P-R keys until the computer restart  - [http://support.apple.com/kb/HT1379](http://support.apple.com/kb/HT1379)
The point is that if the Open Firmware does not recognize the CD Drive, you can't boot from it (even if you can use it in MacOS9 or MacOSX)
If it is like this, the only solution you have, is to boot the Ubuntu Installer from an USB Stick/HD or to try a netboot, the first solution is easier if you are experienced.
You can follow this guide to boot the Installer from USB 
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

