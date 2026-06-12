---
title: "windows install dual boot prob"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by davmil on 2007-06-03
Hi All
I recently installed ubuntu (dapper drake) on my sons desktop.  We have now however decided to make it dual boot but when i try and reinstate windows it sees the hardrive as damaged and wont format it.  I have tried formatting it from linux as a ntfs drive but still no good.  Has the ubuntu install wiped something that windows needs even prior to formatting the drive.  Any suggestions greatly appreciated

David

---

### Post by oilchangeguy on 2007-06-03
> **davmil said:**
> Hi All
I recently installed ubuntu (dapper drake) on my sons desktop.  We have now however decided to make it dual boot but when i try and reinstate windows it sees the hardrive as damaged and wont format it.  I have tried formatting it from linux as a ntfs drive but still no good.  Has the ubuntu install wiped something that windows needs even prior to formatting the drive.  Any suggestions greatly appreciated

David

what version of windows are you trying to use? is the cd a factory restore cd? or a windows only cd?

---

### Post by davmil on 2007-06-04
trying to install xp, the xp disc hangs at setup starting (after loading a heap of stuff). I also tried a windows 2000 install disc i had thinking maybe if i could format the drive with it i might have more luck.  It got further, setup could start, but when started to format it stopped with a message that it couldnt format the drive, couldnt recognise it or disc damaged.  Ubuntu still sees the disc fine so i'm assuming there is nothing wrong with it.

---

### Post by stalkingwolf on 2007-06-04
In My experience you will have to fdisk the drive.  Then repartition and format the drive.  Then install
winblows first, then Ubuntu.  Maybe someone here has an easier way.

---

### Post by davmil2 on 2007-06-05
tried a variety of approaches with fdisk and cant get windows to intall no matter what. Discs ok, tried a couple of windows versions and they dont recognise the hard disk, ubuntu still does so whats been removed in the ubuntu install process that  windows needs?????? This is getting damned frustrating, i'll end up installing a new hard drive at this rate so i stop wasting my time.

---

### Post by stalkingwolf on 2007-06-05
Did you set your windows partition to active.   Check that the HDD is jumpered properly?
Have you tried Gparted to pertition and format the drive?  Or maybe The Ultimate boot CD?  On occasion
I have to use a formatting/partitioning tool from the HDD Manufacturer, Seagate is one that I do.

---

### Post by dstew on 2007-06-05
It is important to differentiate between the words "disk" and "partition". If you are a long-term Windows user, you are used to using the word "disk" to refer to both disks and partitions. For instance, in Windows, people will talk about the C: "disk" or drive, when this is really a partition. In Windows, the default installation will create a single partition that encompasses the entire drive, minus the Master Boot Record, and give it the name "C:". However, Linux carefully distinguishes between disks and partitions. In Linux, a disk has a name like /dev/sda, and a partition has a name like /dev/sda1.

When you install Linux, the installer usually creates two partitions on the disk, a root partition like /dev/sda1, and a swap partition that might be /dev/sda2. Next, the installer formats the partitions, making an ext3 filesystem in the /dev/sda1 partition, and a swap system (not really a file system) in the /dev/sda2 partition. After that, it installs the Linux operating system.

If you now try to install Windows on the disk, the Windows installer will be unable to find any space to install itself. Windows is not able to recognize the ext3 file system, and the disk will look "damaged" to it. The only thing  you can do is let Windows re-format the entire disk, and create its one big partition. Your Linux system will be wiped out. This is because Windows has no respect for other operating systems that might be present.

You can get fancy, and try to make room for Windows by shrinking your main Linux partition, and creating a new partition out of the unallocated space. The Windows installer might see the unallocated space, and be able to create a new partition there, but I doubt it.

The easiest way to create a dual-boot system is to install Windows first, then Linux. If you already have Linux on there, you might have to let Windows have its way first, and wipe out your Linux install, then install Linux again after Windows is working.

---

