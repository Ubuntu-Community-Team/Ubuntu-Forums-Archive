---
title: "Partitioning Question (creating a shared storage drive)"
date: 2008-09-11
forum: Apple Hardware Users
---

### Post by inzania on 2008-09-11
Hey everybody,

I just purchased my first MacBook, but love Ubuntu and want to continue using it... I also need to use Windows occasionally.  So I plan to triple boot, using the tutorials available online.  However, I would also like to create a 4th partition as a "Storage" drive, accessible from all 3 operating systems.  Ideally, my 186gb HD would be separated into:
[40gb - OSX]
[20gb - Ubuntu]
[20gb - Windows]
[106gb - Storage]

I'm attempting to modify the command line usage of "diskutil resizeVolume" in order to accomplish this effect, but I want to make sure I don't make a mistake here, and that my intended effect is logical:
```
diskutil resizeVolume /dev/disk0s2 40G Linux Linux 20G "MS-DOS FAT32" Windows 20G MS-DOS Storage 106G
```
First off, is MS-DOS the right type specification for a storage drive?

Secondly, is this a logical approach to having easy & common access to all my data between OSs?

Thanks!

---

### Post by DGortze380 on 2008-09-11
> **inzania said:**
> Hey everybody,

I just purchased my first MacBook, but love Ubuntu and want to continue using it... I also need to use Windows occasionally.  So I plan to triple boot, using the tutorials available online.  However, I would also like to create a 4th partition as a "Storage" drive, accessible from all 3 operating systems.  Ideally, my 186gb HD would be separated into:
[40gb - OSX]
[20gb - Ubuntu]
[20gb - Windows]
[106gb - Storage]

I'm attempting to modify the command line usage of "diskutil resizeVolume" in order to accomplish this effect, but I want to make sure I don't make a mistake here, and that my intended effect is logical:
```
diskutil resizeVolume /dev/disk0s2 40G Linux Linux 20G "MS-DOS FAT32" Windows 20G MS-DOS Storage 106G
```
First off, is MS-DOS the right type specification for a storage drive?

Secondly, is this a logical approach to having easy & common access to all my data between OSs?

Thanks!

I typically back up my HFS+ partition, resize it to the appropriate size and leave the rest partitioned. Then use Gparted to create everything else.

(Just personal experience) but I've had very little luck with FAT32 in OS X, corrupts constantly, and if you get one accidental removal it's toast (again, just my experience). There are definitely stable NTFS drivers for Ubuntu, and I think there are for OS X... I would go that direction for the share instead of FAT.

---

### Post by inzania on 2008-09-11
> **DGortze380 said:**
> I typically back up my HFS+ partition, resize it to the appropriate size and leave the rest partitioned. Then use Gparted to create everything else.

Hm, I'm a little lost here - you resize the OSX partition into 2 parts, for example 40G for OSX and the rest for a 2nd partition - and then install Ubuntu and use Gparted to split the large partition (where Ubuntu is installed) further, creating a partition for Windows and so on?

---

### Post by cyberdork33 on 2008-09-11
> **inzania said:**
> Hm, I'm a little lost here - you resize the OSX partition into 2 parts, for example 40G for OSX and the rest for a 2nd partition - and then install Ubuntu and use Gparted to split the large partition (where Ubuntu is installed) further, creating a partition for Windows and so on?gparted is on the LiveCD. Create your partitions before you install Ubuntu.

FAT32 (msdos) should work fine although there is a 4GB filesize limitation (meaning a single file cannot be larger than 4GB).

There is a major drawback to your plan though. You didn't account for the EFI partition. 
1. EFI
2. OSX
3.Ubuntu Root
4. Windows
5. Shared
6. Swap

Windows will only be capable of seeing the first 4 partitions, and both Ubuntu root, and windows partitions cannot boot unless they are one of the first four partitions.

---

