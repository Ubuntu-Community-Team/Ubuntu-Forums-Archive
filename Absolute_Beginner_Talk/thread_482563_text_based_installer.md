---
title: "text based installer?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by LouisStDubois on 2007-06-23
This is such an elemental question that I didn't find a thread that addressed it.  O.K. I downloaded the alternate version of Ubuntu or the version that isn't live.  I have an extra hdd that I've formatted FAT32 specifically for Ubuntu to reside on, but I haven't a clue how to install Ubuntu from a "text-based installer" can anyone enlighten me please.  Thank you.  Louis

---

### Post by FleetAdmiral74 on 2007-06-23
have you tried putting in the CD and seeing if you can follow it at all?

---

### Post by BobCFC on 2007-06-23
If you put the CD in the drive then reboot and nothing happens check your BIOS for the order of boot devices.  You want it to boot the DVD/CD drive before the hard disk.  You can always change it back afterwards.

---

### Post by confused57 on 2007-06-23
> **LouisStDubois said:**
> This is such an elemental question that I didn't find a thread that addressed it.  O.K. I downloaded the alternate version of Ubuntu or the version that isn't live.  I have an extra hdd that I've formatted FAT32 specifically for Ubuntu to reside on, but I haven't a clue how to install Ubuntu from a "text-based installer" can anyone enlighten me please.  Thank you.  Louis
There are excellent screenshots of the alternate installer here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You can't install Ubuntu on a FAT32 filesystem,  you'll need to resize your FAT32 to create unallocated space  formatted  ext3 for your root partition and another partition for swap.

---

### Post by louieb on 2007-06-23
> **confused57 said:**
> [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Mega dittos confused57. Just about to point him there too. 

Except for the partitioning part of the install the alternate is the same as the live CD.  they both ask the same questions and you answer them.

---

