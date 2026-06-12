---
title: "Yet another External Hard Drive Problem"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by gray_damascus on 2007-05-16
Well I mounted my EHD and it works out fine...

Problem is that I can't write on my External Hard Drive.
I tried the chmod command in the terminal but it didn't change the permissions in my EHD...

it just says that : changing permissions of 'disk' : Read-only File System

Can anyone help me figure the prob? thx

---

### Post by taurus on 2007-05-16
What is the filesystem of that harddrive?

```
sudo fdisk -l
```

---

### Post by gray_damascus on 2007-05-16
I'm not sure sir, the EHD was a gift to me by my father...

Don't know if this could help sir but I used to use the EHD on a windows XP sir...

Sorry if I can't answer sir... very new sir

---

### Post by gray_damascus on 2007-05-16
it says on the bottom ntfs sir

---

### Post by taurus on 2007-05-16
With ntfs filesystem, you need to install ntfs-3g driver before you can write to it.  Which release are you running right now?

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by gray_damascus on 2007-05-16
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2386    19165513+  83  Linux
/dev/hda2            2387        2432      369495    5  Extended
/dev/hda5            2387        2432      369463+  82  Linux swap / Solaris

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
fidz@fidz-laptop:/media$

---

### Post by gray_damascus on 2007-05-16
feisty fawn sir

---

### Post by taurus on 2007-05-16
```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
sudo umount /dev/sda1
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
ls -la /media
```

---

### Post by gray_damascus on 2007-05-16
thanks sir...

glad to be here on Ubuntu and helped...

thx alot

---

### Post by sdswingr on 2007-08-08
I am having the exact same issue, except my drive is fat32...and the problem just started today, yet I have been able to write to the drive previously...any thoughts...
I am running 6.02


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    c  W95 FAT32 (LBA)

---

### Post by sdswingr on 2007-08-08
any thoughts

---

### Post by gray_damascus on 2008-03-28
what i know is that if it's fat32 sir you could write on it...

hmmm wanna try formatting it to ext3?

if it's for a 'linux-only' sir...
otherwise i have no idea why it won't write... as you probably have checked the permissions sir

---

