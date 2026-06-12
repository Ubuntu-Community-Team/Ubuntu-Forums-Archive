---
title: "In the middle of an install, mount point for second harddrive?."
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Mischief on 2007-01-09
Hi fellas,

I'm in the middle of the Ubuntu install and I thought I had the partitioning figured out.

Here's the problem:
I'm on step 5/6 in Gparted.

[sda1] /media/sda1 - NTFS - Windows XP 40gb
[sda2] /home - EXT3 - Shared data 87 gb
[sda3] / - EXT3 - Ubuntu Install 20 gb
[sda4] /swap - EXT3 - Linux Swap 3 gb
[sdb1] ??? - EXT3 160 gb

What do I choose for "mount point" for the second hard drive [sdb1]?
This is going to be the second "shared data"-drive. Should it be /home too?

Please help!

---

### Post by meng on 2007-01-09
It can be anything you want, but it can't be the same as another device's mountpoint. So it can't be /home

My suggestion:
/media/sdb1

More imaginatively:
/media/shared
/media/otherdrive
/home/shared
/home/data

By the way, you can always change the mountpoint later by editing your /etc/fstab

---

### Post by Mischief on 2007-01-09
Ok, thanks a lot!

That brings me to another question.
The Windows partition is listed as [sda1] /media/sda1, should it be "/boot"?

---

### Post by meng on 2007-01-09
No! Just leave the Windows partition mountpoint as it is!

---

### Post by taurus on 2007-01-09
> **Mischief said:**
> Ok, thanks a lot!

That brings me to another question.
The Windows partition is listed as [sda1] /media/sda1, should it be "/boot"?

It's a Windows partition so it cannot be /boot.  Just leave it where it is, /media/sda1.

---

