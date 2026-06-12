---
title: "Triple boot  Windows XP, 7,   Ubuntu issues"
date: 2012-06-04
forum: Any Other OS
---

### Post by Happytyper on 2012-06-04
Hi, Im having a similar issue and I can't seem to fix the problem.
I am thinking it might have something to do with installing the GRUB bootloader on the same partition as my windows install.
sda1 = Windows XP
sda2 = Windows 7
sda3= Ubuntu 12.04

Installed in that order.
Would it be easier to move GRUB  to sda3 and then specify boot files on each of the windows partitions?

---

### Post by oldfred on 2012-06-04
Moved to other os & your own thread as issues is different with triple boot and possible install of grub ot Windows partition.

You never install grub to a NTFS partition as a NTFS partition has to have NTFS boot info in it.

Run this so we can review what is where and post link to run of Boot-Info.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

To understand Windows multi-booting:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Happytyper on 2012-06-04
Hey oldfred,

Thanks for the speedy reply & help. Had a good read through the multibooters article, broadened my understanding a bit.
Ran the boot-repair utility and here we are;
[http://paste.ubuntu.com/1024142/](http://paste.ubuntu.com/1024142/)

I was mistaken, its actually sdb not sda, it must have switched when I plugged in my second storage drive.

Cheers.

---

### Post by oldfred on 2012-06-05
Your NTFS partition sdb1 has this:
```

    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 899936928 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.

```You can repair the NTFS boot sector with these commands if you only installed once. NTFS keeps a backup and testdisk can restore the backup.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

You have Windows boot loader in the MBR of both drives. You have both operating systems on the same drive, but have to have grub2's boot loader in the MBR to boot Ubuntu & Ubuntu will let you boot into the Windows active/boot flag partition. From that you will get the choice to boot either Windows.

You should be able to use Boot Repair to install the grub2 boot loader to the MBR. Make sure you have that drive set in BIOS to boot.

I generally prefer to have an operating system on every drive or at least one on each drive if you have more than one drive. And configured with all the system files, boot loader, etc so each drive can boot without the other.  If one drive fails you then can boot the other even if you get an error message about data partitions or other partitions from the broken drive not loading.  I also like to have multiple repair CD, but now have changed to USB flash drives and have one with a full install to use as another drive if need be.

---

### Post by Happytyper on 2012-06-05
It just occurred to me that the Windows bootloader installed on sda is from the previous install of windows. It doesnt actually have an OS on it though. I just used that drive to backup everything while I installed all 3 operating systems on sdb. 
Not sure if this changes anything.

In repairing it, are we going to move grub to the sdb3 partition?

---

### Post by Happytyper on 2012-06-05
That worked a charm,
Had to run boot-repair though to get GRUB back up again though.

Grub displays; Ubuntu (sdb5), Windows 7 (sda1), Windows 7 (sdb1)

I'll have to fix that up on sda1 so its no longer recognised. However, Im wondering whether it is possible to revert Windows XP back to its original loader and windows 7 has its own on sdb2 then have 3 options on Grub; sdb5, sdb1, sdb2.

Currently I have to select sdb1 then select windows xp or 7 after that on another menu.

Thanks for the help.

---

### Post by oldfred on 2012-06-05
You can split the boot files.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

But you may have to repair each separately with the XP Install and Windows 7 RepairCD. But Windows only repairs the partition with the boot flag. So you would have to set boot flag on XP and repair it, then move boot flag to Windows 7 and repair it. This only works if both installs are primary partitions as Windows will only boot from a primary partition, but a second install can be in a logical as it still boots from the primary.

---

