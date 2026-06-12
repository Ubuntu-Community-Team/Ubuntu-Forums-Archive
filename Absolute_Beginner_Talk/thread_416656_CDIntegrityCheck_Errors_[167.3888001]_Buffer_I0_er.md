---
title: "CDIntegrityCheck: Errors [167.3888001] Buffer I/0 error on device sr0, logical block"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by XYZ1 on 2007-04-21
Hi,
I tried to install the latest "ubuntu-7.04-desktop-i386.iso" on a Compaq EVO D510 with the following specs:
*Intel Pentium 4 2.4Ghz
*512MB RAM
*40GB HD (the HD has only 1 partition with Windows XP Professional SP2)

I also tried the previous Ubuntu release but had exactly the same problem.

I followed exactly these steps from the "BurningIsoHowto":
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
1. MD5 Checksum -> was OK
2. Burned the ISO using InfraRecorder as explained - was succesfull
(I also burned it at a lower speed and on other CD-R's, but still the same issue.)

But it didn't pass the "Installation/CDIntegrityCheck":
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

I always get these errors:
[   167.3888001] Buffer I/0 error on device sr0, logical block 0
[   167.3888052] Buffer I/0 error on device sr0, logical block 1
[   167.3888096] Buffer I/0 error on device sr0, logical block 2
...

As expected it's also not working when I try to Start/Install Ubuntu instead of doing the "Installation/CDIntegrityCheck"


I tried the "CDIntegrityCheck" and the "Start/Install" on an Pentium M Notebook and it was fine. So the disc is definately OK.
There must be something wrong with the Compaq EVO D510. Is it the CD-ROM drive?


Any ideas?


THX

---

