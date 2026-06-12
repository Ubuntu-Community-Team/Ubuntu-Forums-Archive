---
title: "unable to boot"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by .:mike:. on 2007-04-09
I have just installed edgy to a new sata drive but i cannot boot into xp or ubuntu.
When i try to boot ubuntu it says error 17 cannot mount selected partition and when i try to boot xp i says error 12 invalid device requested. 

The only way i can get any thing to boot is if i use the super grub cd. 

Thanks for any help and please go easy im new to linux  :)

---

### Post by PurplePenguin on 2007-04-09
I'm impressed!  You say you're new to linux, but you've already picked up tricks like using the Super Grub Disc... great instincts!

OK, if I recall correctly, grub error 17 means that grub can't identify the filesystem type properly.

If you boot in with a live cd or the Super Grub Disc, can you type in and post the results of:
```
sudo fdisk -l
```

It might be a good idea to boot in with the live CD and run fsck on your main Ubuntu partition (replace hda1 with the proper partition), as well
```
sudo fsck /dev/hda1
```
Just make sure you boot with your Ubuntu CD, not the Super Grub Disc, since you don't want your Ubuntu partition to be mounted.

[Here's a really long thread about restoring GRUB. ]("http://ubuntuforums.org/showthread.php?t=224351") Take your time and scan through it - getting to know grub will make your life with linux a lot easier.

---

### Post by .:mike:. on 2007-04-09
This is what i get when i type sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        3922    31495432+   f  W95 Ext'd (LBA)
/dev/hda2   *        3923        7871    31720342+   7  HPFS/NTFS
/dev/hda3            7872        9728    14916352+   7  HPFS/NTFS
/dev/hda5               2        3922    31495401    b  W95 FAT32

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

thanks for the help just about to try and run fsck.

---

### Post by .:mike:. on 2007-04-09
fsck just says
fsck 1,39 (29-may-2006)
ezfsck 1.39 (29-may-2006)
/dev/sda1 : clean, 98921/9584640 files
775451/19159512 blocks 

not sure if thats good or bad??

---

