---
title: "I installed Windows and now Grub doesn't load..."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by sargonious on 2006-11-05
I installed Windows XP Home Edition and now I can't boot to Linux. I'm stuck in Windows. I partitioned my hard drives and everything then Installed Windows onto the FAT32 Partitions leaving the Linux partitions untouched. How do I get Linux back up without erasing anything??? HELP!

---

### Post by ReaderRat on 2006-11-05
ReInstalling Windows & Recovering Ubuntu
          [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
     OR - [http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by sargonious on 2006-11-05
It didn't work. I tried the sudo grub... yada yada... no go. It just boots directly to Windows XP.

---

### Post by bobpur on 2006-11-05
It took me a while to learn that when you dual boot, you install windows first. If you install windows last, it overwrites grub. You can see firsthand what happens when you do that.
Fortunately, for me, I wasn't doing anything with that computer and re-installed things in the proper order and went on about my business.
For what it's worth, [www.distrowatch.com](www.distrowatch.com) has an OS called "system Rescue" that has tools to help with your problem. It's currently about #97 on the distro list if you want to look at it. I burned a copy for future use, but haven't done anything with it yet.

                           Good Luck!

---

### Post by seshomaru samma on 2006-11-05
The system rescue CD is indeed very good- it's Gentoo based
([http://www.sysresccd.org/Download](http://www.sysresccd.org/Download))

Did you follow the steps offered in ReaderRat's second link?
If so ,what was the output ?
Did you get any errors?

Which partition did you install Windows on?

If you burn the SysRescue CD you can boot from it (it's much faster than Ubuntu live CD)
and run these commands:
> grub
find /boot/grub/stage1
root (hd?,?)
(change the ?,? to whatever the output of the second command is)

> setup (hd0)
quit

---

### Post by JayTee on 2006-11-05
I downloaded the Super Grub Live CD from here: [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)  

 It boots linux off the CD and lets you reinstall grub. Then all you should need to do is reboot and it'll find your old /boot/grub/menu.lst file. You'll have to edit it to add the Windows install. Just add the following to the bottom of your menu.lst file to add a Windows boot option.

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows 
root		(hd1,0) #this needs to point to your Windows disk & partition
makeactive
chainloader +1

---

### Post by sargonious on 2006-11-06
The file is "bz2." What kind of extension is that? I downloaded the file but what is it? Is it a compressed file type? What can open it?

---

### Post by ReaderRat on 2006-11-06
Yes, it is a compressed file. You can extract it by going into Nautilus file browser and double clicking on it.

---

### Post by sargonious on 2006-11-06
I restored Grub but now Windows is gone. I'm trying to add it to the menu.

---

### Post by sargonious on 2006-11-06
I have 2 hard drives.

The first one has 30 GB.

The second one has 10 GB.

The first partition is Ubuntu 19GB, second is 1GB Linux Swap.

The third partition is Windows XP NTFS, the fourth is very small 650mb FAT32.

The sond hard drive is partioned 4GB Ubuntu mounted to Home, 4GB FAT32, and the remaining 2GB is Windows Swap (something I did myself).

How do I give Linux Access to the Fat32 Drives without having to constantly do it manually by going to the disks-admin? I want to share certain files between WinXP and Linux. Plus I don't seem to have full access to the partitions. I can only read.

---

### Post by Sef on 2006-11-06
> How do I give Linux Access to the Fat32 Drives

Linux and Windows can both read FAT 32 paritions.  If you can't access the FAT 32 partition, then it sounds like you have a permission problem.  I will need to let someone handle how to do that.

---

### Post by sargonious on 2006-11-10
How can I permanently mount my fat32 drive so I can always access it read/write?

---

