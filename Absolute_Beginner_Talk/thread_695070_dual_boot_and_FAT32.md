---
title: "dual boot and FAT32"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by blairm on 2008-02-12
hi,

Dual-booting XP and Ubuntu for the first time, and want to have documents accessible (ie read and write access) from both operating systems.
From what I've read, will ned to set up a FAT32 partition to allow this, but have a couple of (embarassingly newbie) questions...

1) all the guides I've seen use QT Parted or similar to create the FAT#@ partition; does the tool on the live cd not do the job?

2)once FAT32 is created, will documents automatically go there or will I need to direct them?

3) a more general partitioning question, as I've always used the auto option; how should I split up a 160gb hard drive? Every site I've seen seems to have different ideas.

Thanks in advance,

Blair

---

### Post by blairm on 2008-02-12
Oops, caps key got stuck... that should of course be FAT32!

Blair

---

### Post by smartboyathome on 2008-02-12
1) The CD does do it, just use GParted (System > Administration > GNOME Partition Manager). QT Parted should only be used with KDE imo.
2) You need to direct them there by using the Manual partitioner in the installer. Set its mount point to /home. As a side note, I would use GParted to do your partitioning before using the installer.
3) I would say 40gigs: Ubuntu, 40gigs: XP, and then the rest would be for docs and such.

---

### Post by zozobra on 2008-02-12
Hey Blair. A good way to do this would be to have a separate partition accessible to both Windows and Linux that contains all of your share documents/media. So, you would install Windows first with a small partition large enough to contain the OS (~4-6GB for XP). Next, create the Linux partitions. You can either set up a separate home partition (formatted with the ext3 filesystem) in which Ubuntu will hold your user information and also use that as the shared partition between Linux and Windows OR keep the home directory inside the default bootable Ubuntu partition and set up a separate ext3 partition for your media. You would then boot to Windows and install the driver from [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) that lets Windows access ext2 and ext3 file systems. Now, Ubuntu and Windows can both access the ext3 partition of your choosing.

---

