---
title: "rescue my data before i format...."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by phydreamer on 2008-04-16
First i had problem with grub "error 17" but after several tries didn't work...
So i tried Super grub disk ,didn't work either... After a while (by my mistake) i started playing around with the option of the S.G.D and i think i've done it worse..
i dont have windows installed only ubuntu but because of playing around some thing might not be what it looks like...:(

a guy on irs told me that i'm  missing a partition starting at block 1 and ending at block 14216 type ext3... whatever that means...


the out put from  sudo fdisk -l is

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe464e464

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4997    40138371    7  HPFS/NTFS

```

i only want to save some data or at least my email accounts(only passwords) some help?

---

### Post by phydreamer on 2008-04-16
sdb is just an empty external disk hopefully to use it for saving...

---

### Post by phydreamer on 2008-04-16
bump

---

### Post by Zralou on 2008-04-16
Your sdb is marked with a bootable flag, so its possible the grub is installed there, and if its a removable drive, that will screw up the boot sequence.

Sara Lou

---

### Post by philinux on 2008-04-16
From the fdisk output you've not got root or home. Maybe the live cd could get some data of there.

---

### Post by phydreamer on 2008-04-17
> **Zralou said:**
> Your sdb is marked with a bootable flag, so its possible the grub is installed there, and if its a removable drive, that will screw up the boot sequence.

Sara Lou

i dont think so because its empty....

---

### Post by phydreamer on 2008-04-17
> **philinux said:**
> From the fdisk output you've not got root or home. Maybe the live cd could get some data of there.

ok so how i will procceed?

---

### Post by bumanie on 2008-04-17
Your fdisk -l is showing that you only have a swap aprtition on sda1, the rest of the filesystem has disappeared. Looks as though you'll have to do a reinstall of the file system. As you have to do that, it would be a good idea to choose manual at the partitioning stage and create a separate /home partition so if something like this happens again, your data in /home should be safe. I can't imagine you have any data on sda1 as there is only the swap partition. Also as swap has a boot flag it would probably be a good idea to format the whole of sda1 and start from fresh. As windows is on sdb1, it should be OK, but windows prefers to be on the first disk, but still can boot from the secondary disk, but this often involves editng of /boot/grub/menu.lst. May be you should read this  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) It's a lot to read, but very informative about grub - it includes trouble shooting for grub errors also - may not help now, but good information to have for the future.

---

### Post by Traceur-UK on 2008-04-17
You could try booting from an Ubuntu Live CD and mounting the drive, then recovering any data you need (and, say, burning it to a CD or a removeable medium)... then do a reinstall.

---

### Post by phydreamer on 2008-04-17
i gave up.....reinstall after all

---

