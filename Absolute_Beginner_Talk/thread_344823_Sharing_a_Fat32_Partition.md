---
title: "Sharing a Fat32 Partition"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by spudgunner on 2007-01-23
So there are no Linux drivers for my printer, I have to keep Windows on my computer... I had an 80GB hard drive. I'm going to partition 15GB to Windows, 15GB to Linux, 1GB to Linux Swap Drive, and the rest (minus a little for the MBR) to a Fat32 partition. I want to be able to access the Fat32 drive from both Ubuntu and Windows... it'll work fine with Windows, I tried this with Knoppix and it didn't work out too well... so yeah, how do I do it with Ubuntu? And will Ubuntu automatically update the MBR to switch between Windows and Ubuntu?

---

### Post by meng on 2007-01-23
You should be able to access the FAT32 partition from Linux. Ubuntu will overwrite the MBR so that you can choose between Windows and Ubuntu at boot-time.

---

### Post by Juan Largo on 2007-01-23
Ubuntu can access FAT32 partitions no problem.  In fact, I know it will access NTFS as read-only.  During the installation, you have to provide "mount points" for all your partitions.  These will be displayed as icons on your desktop.  To mount a partition, just click on it -- it's that simple.

As far as the boot loader is concerned, yes Ubuntu will install GRUB over the MBR.  It *should* detect your Windows partition and provide you with a dual-boot system.  However, this can go very wrong in some cases, depending on how many hard disks you have, which one Ubuntu is installed on, whether you do the partitioning ahead of time or during the Ubuntu install, etc., etc.

Actually, I think it's very bad for any OS to take "ownership" of the MBR, and Windows is certainly guilty on that count also.  Automatically taking over the MBR can sometimes lead to unintended consequences, for example if you've combined SATA and IDE hard disks on the same motherboard.  It's much better to modify the boot loader that came with the computer than install another one.  There's some important stuff on the MBR that should not be tampered with IMO.

---

### Post by spudgunner on 2007-01-24
Thanks, that helps... one last question... the Fat32 will be read/write be default, no?

---

### Post by bodhi.zazen on 2007-01-24
> **spudgunner said:**
> Thanks, that helps... one last question... the Fat32 will be read/write be default, no?

You may need to edit fstab.

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: vfat (FAT) use umask=000

---

### Post by houstonbofh on 2007-01-24
You can also install the Windows driver for the linux filesystem. [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Juan Largo on 2007-01-24
By default, Ubuntu *should* be given read/write access to FAT32 partitions.  Editing fstab is always a fall back option if the default fails.

---

