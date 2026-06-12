---
title: "problem with second hardrive - please help"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Koalaborg on 2007-12-08
Hello.
I am having difficulties with my secondary harddrive, which is NTFS, and contains all of backup data from when I was running windows. So obviously wiping the drive and partitioning it isn't an option. 

Previously, when I had installed Kubuntu, I had no problem, upon installation,  mounting this drive. However I recently had to reinstall, and wasn't able to mount it during install. For some reason, I could see it showing up in install screen as dev/hdb, but I couldn't select it. Anyway, I went ahead with install figuring I could just mount later, but I can't even see it showing up when I do 
sudo fdisk -l, or when I search media. Only my dev/hda partitions show up. 

I double checked the disk,wires are correct, etc and it shows up at the boot screen as primary slave, so I'm a little lost as to what to do next besides perhaps try to reinstall again.

I'm still pretty new at this, but would really appreciate the assistance.

---

### Post by cmnorton on 2007-12-08
It sounds like you need to mount the drive, first by hand, and then get its mounting into fstab. Offhand, I don't know what an ntfs mount entry looks like in /etc/fstab. You could probably get a hint by mounting a memory stick that's formatted FAT32.

---

### Post by logos34 on 2007-12-08
if it's not showing up in fdisk or

sudo lshw -C disk 

then it's not being detected period--manually trying to mount it won't help.  

Check the hard disk settings in the bios--make sure it's set for [auto] detect, or if it is try [usr] with the appropriate parameters (check product page)

---

### Post by Koalaborg on 2007-12-13
sorry its been several days since I have been able to be at my computer. thanks for the input.

I can clearly see my second harddrive during bootup when I go into Bios - it is set for [auto] detect. it doesn't show up when I do sudo fdisk:
> 
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices) 

however it looks like a second drive is showing  up with sudo lshw -C  disk as disk1, but the size doesn't match my second drive :

> 
  *-disk:0
       description: SCSI Disk
       product: WDC WD800JB-00ET
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 77.0
       serial: WD-WMAHL1502367
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       size: 8062MB 

I don't think I understand the difference between sudo fdisk and sudo lshw -C disk and why it would show up a second drive.

---

