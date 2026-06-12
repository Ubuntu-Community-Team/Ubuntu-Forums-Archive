---
title: "Unmonut harddrive with XP on it?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by bubi1980 on 2006-09-24
Is it possible to unmount a harddisk with windows XP on it, and still keep XP working?
I would like to reinstall ubuntu, but had a problem and want to try it with unmounting.

---

### Post by bulldog on 2006-09-24
I'm not sure what you mean by unmounting XP.

It has nothing to do with eachother.

---

### Post by bubi1980 on 2006-09-24
is "unmounting" something like delete a partition and make new one?

---

### Post by bodhi.zazen on 2006-09-24
aptitude -f remove windows_xp

---

### Post by ironslave on 2006-09-25
i got it figured out so far... this topic is good to go for me :) fstab was still registered to find the freakin non existant NTFS partitions i deleted

---

### Post by bulldog on 2006-09-25
> **bubi1980 said:**
> is "unmounting" something like delete a partition and make new one?

Nope,unmounting is making it unreachable and unreadable,no access.
The unmounted partition will not change at this action,don't worry.
But there's no reason to unmount anything when you do a fresh install.

---

### Post by louieb on 2006-09-25
I don't know about unmounting your xp hard drive. But the first time I installed Linux I wasn't sure of what I was doing so I unpluged my win xp drive before running the install. 
After the installation I plugged the drive back in, created an xp entry in the grub.conf aka menu.lst file. Both Linux and xp worked.

---

