---
title: "Error:  Couldn't mount device '/dev/hda1': input/output error"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Miller on 2007-01-18
Hello,  
I am trying to install Ubuntu with the Ubuntu installer on my boot disk.  Everything goes fine until i get to step 5 and try to partition my hardrive.  I click Forward after i select 50 Gb as my partition size.  It waits several minutes and then leaves me on the same screen.  I tried to manually partition with the 3rd option and i got the error  "Couldn't mount device '/dev/hda1': input/output error".  
Thankyou for any advice.

---

### Post by Tomosaur on 2007-01-18
Please open up a terminal and paste the output of:
```

fdisk -l

```

---

### Post by taurus on 2007-01-18
Does it already have XP on the drive?  Boot into XP and defrag the harddrive a few times (go for three).  Then, boot up the LiveCD and use gparted to resize it again.

---

### Post by Miller on 2007-01-18
it already has XP on it.  Im trying to do the FDisk command in the terminal.  Do you just want what is says after i put in Fdisk -?  I'll post what i got for that right now.

usage fdisk [-l] [-b SSZ] [-u] Device
E.g.: Fdisk /dev/hda (for the first IDE disk)
or: Fdisk /dev/hda (for the third SCSI disk0
or: Fdisk /dev/eda (for the first PS/2 ESDI drive)
or: Fdisk /dev/rd/c0d0 or Fdisk /dev/c0d0 (for raid devices)



Im sorry if there are any mistakes in that.  It wasnt a direct copy and paste.  I havent got my wireless internet connection working on the Ubuntu yet.

---

### Post by taurus on 2007-01-18
It should be

```
sudo fdisk -l
```

---

### Post by Miller on 2007-01-18
i ran sudo fdisk and i am unable to give you the whole list at the moment.  It said it was unable to open /dev/hda1 if that is any help.   Im running in between two comps so its kinda tricky to get all of the code it said.  I will work on it though.

---

### Post by kerpal on 2007-02-07
I get this same error whenever I try to manually install and select my 300 gb Seagate drive, which is SATA and has only 1 partition using up most of the space as a windows xp NTFS partition. It also has about 10 gb or so of unused free space which I want to allocate for ubuntu. I can't even see either the partition or the unused space, but the drive and the size is detected.

here is a paste of sudo fdisk -l


Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         542     4353583+   7  HPFS/NTFS
/dev/hda2             543        7299    54275602+   f  W95 Ext'd (LBA)
/dev/hda5             543        7299    54275571    7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   42  SFS

If it helps my other drive is an IDE and that one detects perfectly fine despite being 2 NTFS partitions as well, but I cannot mount or even see the partitions on this drive.

---

