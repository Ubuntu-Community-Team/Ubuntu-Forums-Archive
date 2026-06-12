---
title: "[SOLVED] Install on Ssystem with two HD's"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by CasPol on 2007-12-18
Hi there;

I would like to install UBUNTU 7.10 on a system with two hard drives. One Hard drive ( master) has XP on it the second Hard Drive ( slave) is empty formatted and ready for use with UBUNTU. In addition I would like to be able to dual boot.

How do I go about it ?

Many thanks.

---

### Post by hyper_ch on 2007-12-18
- are they both IDE or SATA or are they mixed?

- best for installation if to NOT format the disk you want to use for ubuntu at all. If you already did format it to ntfs /fat32 just delete it ;) OR you setup your partitions manually ;)

---

### Post by the Didey on 2007-12-18
You need to get the LIVE CD and install from there.

There's a sticky on the front page of the beginners section.

[the complete guide to installation in ubuntu]("http://ubuntuforums.org/showthread.php?t=500020")

If the second drive is totally free you can pretty much plug in the LIVE CD and follow the installation instructions from there.

There's also a utility to check the integrity of the LIVE CD on the LIVE CD

---

### Post by louieb on 2007-12-18
confused57 wrote this guide a while back. It has all the basics. 
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")
the nice thing about using a separate drive for each OS is if one goes out you can always boot the other.  :mad:
One thing you'll need to note - if you have IDE drives and  you want to keep your XP drive untouched it will need to be moved to the slave position.

---

### Post by CasPol on 2007-12-18
Thanks al lot all, grat tips and advise...

do I change the level ( master/slave) before or after the UBUNTU install ?

---

### Post by louieb on 2007-12-18
> **CasPol said:**
> do I change the level ( master/slave) before or after the UBUNTU install ?
Easier if you do the swap before. - That way when GRUB is installed It will set up the configuration  (/boot/grub/menu.lst) to boot XP off of the slave drive. 
IF you do it after you'll have to manually alter the configuration yourself.

---

