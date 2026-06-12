---
title: "rEFIt says Missing Operating System when I choose Linux..."
date: 2010-10-17
forum: Apple Hardware Users
---

### Post by MountainX on 2010-10-17
Someone suggested this step:

> Using the Desktop installer rescue option, just reinstall grub

The 11,1 iMac will not boot up a Desktop/LiveCD. I do have an Alt CD.

Where exactly should I reinstall grub?

---

### Post by ZeroLinux on 2010-10-17
> **MountainX said:**
> Someone suggested this step:
Where exactly should I reinstall grub?
To the partition where "/" is (for example sda2)
It depends how you partitioned you disk 
(I suppose that you didn't make any special "/boot" partition)
After it rEFIt will see boot loader.

---

### Post by MountainX on 2010-10-17
> **ZeroLinux said:**
> To the partition where "/" is (for example sda2)
It depends how you partitioned you disk 
(I suppose that you didn't make any special "/boot" partition)
After it rEFIt will see boot loader.

Thanks but that didn't work. I installed Ubuntu to sda4 and I put grub there too. I also tried grub-install to sda. Grub will not install without the bio-grub partition (sda3 in this case). But I had to delete sda3 because having it causes an "overlapping partitions" error (related to rEFIt).

---

