---
title: "Two hard disks Two OS"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by saiinch on 2007-03-29
i have two hdd in one hdd i have installed ubuntu and in other i have installed xp, i want to know is there any software or way, i can use both hdd at onces with boot options, so i can choose which os to load, so it will also make me to access ubuntu drive from xp and xp from ubtuntu.
thanks

---

### Post by justin whitaker on 2007-03-30
> **saiinch said:**
> i have two hdd in one hdd i have installed ubuntu and in other i have installed xp, i want to know is there any software or way, i can use both hdd at onces with boot options, so i can choose which os to load, so it will also make me to access ubuntu drive from xp and xp from ubtuntu.
thanks

You can modify ntldr to display other OSes on the system, and allow you to select them, you can use something like BootMagic....or you can install GRUB or LILO in the MBR of the XP disk, and make sure that the XP partition can be booted from it. 

As for being able to see NTFS from Linux, well, ntfs-3g works pretty well, and gives you read and write access to NTFS formatted drives. 

From XP, it is a little trickier, but this application [http://www.fs-driver.org/](http://www.fs-driver.org/) works well.

---

