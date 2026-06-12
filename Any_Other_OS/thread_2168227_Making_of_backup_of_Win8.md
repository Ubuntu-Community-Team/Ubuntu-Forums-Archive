---
title: "Making of backup of Win8"
date: 2013-08-16
forum: Any Other OS
---

### Post by jason13 on 2013-08-16
I have a brand new lenovo laptop I want to convert into a dual boot machine. usability and stability are my main goals. I need windows because I'm going into programming and gaming. Right now the file system is a mess, the main drive has 6 partitions (gparted can't tell which are primary or extended) The lenovo utility lets you make a backup of windows to a USB drive. I am trying to figure out the right steps to getting to the end point. The laptop has a 1 TB HDD and a 24 GB SSD. the SDD seems to be mostly unoccuped. I would like to have both OS (or at least Ubuntu) running from the SSD (else, windows gets it's own partition and the majority of the HDD is an NTFS that both can access) and would like to use GRUB as my bootloader. Since I don't have the Win8 recovery disk I need to know if the utility backup is sufficient to reinstall windows, and if keeping the recovery partition is a good idea.

---

### Post by Bucky Ball on 2013-08-16
*Thread moved to **Ubuntu, Linux and OS Chat**.*

While it's possible you may get some help here, you might have more luck on a Win forum. The ***Installation & Upgrades*** sub-forum concerns installations and upgrades of Ubuntu. This thread concerns the manipulation and resizing of Windows partitions. The Win OS partition should NOT be resized in Linux at all. Use Win softwares to recover/resize.

Frankly, easiest to run the recover partition, put Win8 on a small partition (40Gb should be enough) and leave the rest free space. Boot from the Ubuntu install CD, choose Something Else at the partitioning section and partition the free space manually.

This will require researching Ubuntu installation and making a definitive plan (preferably with a pen and paper) regarding how you want the hard drive(s) partitioned/setup. If you turn the free space into one, large extended partition, you imagination is your limitation. You can put as many logical partitions inside an extended as you like. Ubuntu will need:

/ = OS
/swap = pagefile in Win speak

... at the very least.

---

### Post by oldfred on 2013-08-16
Also make a Windows repair flash drive.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Ultrabooks have additional issues with dual video and the Intel SRT which has RAID to use SSD as cache for Windows. See link in my signature for a lot more info.

With Windows 8 pre-installed you have gpt partitioning which only has one type of partition, no primary nor logical.


  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
      
  [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

---

### Post by coffeecat on 2013-08-17
Support, not chat thread.

*Thread moved to **Other OS/Distro Support**.*

---

### Post by buzzingrobot on 2013-08-17
You may have seen this, but here is Lenovo's explanation of creating a Win8 recovery USB and then restoring from it: [http://support.lenovo.com/en_US/downloads/detail.page?DocID=HT076024](http://support.lenovo.com/en_US/downloads/detail.page?DocID=HT076024)

---

