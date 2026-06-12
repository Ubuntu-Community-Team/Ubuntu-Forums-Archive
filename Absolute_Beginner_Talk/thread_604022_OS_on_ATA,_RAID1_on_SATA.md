---
title: "OS on ATA, RAID1 on SATA"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Waitrose Carpark on 2007-11-05
Hi there

I have Ubuntu server 7.10 on an ATA disk. I want 2 sata disks on a raid array that I want to make Raid 1. How the hell do I set this up? Ubuntu boots fine on the ATA disk, I have configured the SATA raid in the bios but it shows up as 2 disks in ubuntu?!?

Thanks!

---

### Post by overdrank on 2007-11-06
> **Waitrose Carpark said:**
> Hi there

I have Ubuntu server 7.10 on an ATA disk. I want 2 sata disks on a raid array that I want to make Raid 1. How the hell do I set this up? Ubuntu boots fine on the ATA disk, I have configured the SATA raid in the bios but it shows up as 2 disks in ubuntu?!?

Thanks!

Maybe these links will help
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[http://ubuntuforums.org/showthread.php?p=3300284#post3300284](http://ubuntuforums.org/showthread.php?p=3300284#post3300284)
Good luck!

---

### Post by psusi on 2007-11-08
See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for information on your hardware.  

I would suggest you just disable the bios fake raid support and set up a conventional software raid with the drives in the installer from the alternate cd.

---

