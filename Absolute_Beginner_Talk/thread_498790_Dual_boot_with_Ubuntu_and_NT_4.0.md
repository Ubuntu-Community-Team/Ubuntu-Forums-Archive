---
title: "Dual boot with Ubuntu and NT 4.0?"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Ian Adkins on 2007-07-11
I want to put together a dual boot system with Ubuntu and Windows NT 4.0 Workstation.  NT 4 isn't my first choice -- I had a copy of Windows 2000 Professional, but after years it's a bit dinged up and I don't care to sink $150 for a legit copy when legit copies of NT 4.0 can be had for $10.  My question is two-fold: (1) what issues should should be aware of with NT, in terms of NT and Ubuntu getting along, running current Windows apps, etc., and (2) what procedure do you suggest for setting up the dual boot on a blank hard drive?  I've read elsewhere that it's best to install Windows first, shrink the Windows partition using the Windows partition manager, run the Ubuntu live CD, disable the Windows partition, and then run Ubuntu setup on the remaining part of the disk.  Thank you!

---

### Post by p_quarles on 2007-07-11
Caveat: I haven't tried dual-booting NT4 with Linux, but I'm fairly certain that the same procedures hold true for any version of Windows.

1) Windows and Linux don't really have any need to "get along." As long as they're on their own separate partitions, and as long as Ubuntu is able to install GRUB, it will work fine. 

2) Yes, install Windows first, but don't use its partition manager. Instead, be sure to defrag the hard drive after installing Windows, and then boot from the Ubuntu CD. The CD contains a partition editor called gparted, which will allow you to set up your dirve exactly the way you want it. The general guideline is at least 10 GB for Ubuntu, and preferably a lot more if you plan on using it as your main OS.

---

### Post by Ian Adkins on 2007-07-12
Thanks!  I'll give it a whirl and let you know how it turns out.  :D

---

### Post by longlegs on 2007-07-12
Hi !
YOU PROBABLY KNOW IT ALREady but keep in mind that NT4 cannot see USB, and has no device manager.
Good Luck!
longlegs

---

