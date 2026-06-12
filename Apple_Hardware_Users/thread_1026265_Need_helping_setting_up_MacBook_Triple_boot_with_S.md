---
title: "Need helping setting up MacBook Triple boot with Shared Data partition"
date: 2008-12-30
forum: Apple Hardware Users
---

### Post by HellLord on 2008-12-30
Hi all, So i may have missed this in the forums or in all the searches or in all the guides so excuse me if its already been asked/resolved.

I've read multiple guides on gparted, gpt/mbr dual partition table implementation methods, and macbook triple boot methods.  I have been successful at this, even though it can be most painful and has to be done in some very specific methods/process orders.

I've got a 465GB drive in my macbook and want to have triple boot of Ubuntu Intrepid Ibex, OS X 10.5.6 and WinXP SP3 WITH a separate Data/Files partition that all three can access, be it ReiserFS, FAT32 or NTFS(3G).  I have tried setting up NTFS-3G and other helpful software to resolve this.   I've tried multiple methods, such as creating all the partitions with disk utility, then installing the OS's.  I've tried using Boot camp to partition a size big enough just for the windows partition and then splitting the mac partition to fit/create a ext2 and swap partition for linux, that worked, but then i couldn't add a separate partition.
  It would seem these issues seem to stem from a number of things, no more then 4 primary partitions for windows, no logical partition in os x and i forget the issue in linux.  correct me if im wrong on those by the way.
 I have spent many hours the last couple weeks trying to set this up and am at the point of asking for help.

I simply want to have a functional HFS+ partition for OS X, a NTFS partition for windows, a ext2 partition for linux, and have to have the EFI partition for boot loader/os x to function correctly as i understand it.  how then could i add one last partition to have shared access to data thats stored on a separate partition.

If anyone has been successful or knows the right way to go about getting this setup to work please let me know how, be specific if you can please so i can reproduce this setup.  Thanks in advance.

---

### Post by pxwpxw on 2008-12-31
I cant be specific without testing.

There are some good ideas in billbear's thread, listed in 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
Link down at the bottom of the page -
Quad-Boot: MacOS/Vista/XP/Linux - post #4 but read the others.
[http://forum.onmac.net/showthread.php?p=12290&postcount=4](http://forum.onmac.net/showthread.php?p=12290&postcount=4)

You might be able to apply some of this your triple boot also, giving you a bonus extra partition in place of Vista. The issues with Vista and XP fighting each other do not apply in you case.

Main points - 
- Initial partitioning using MacOSX Disk Utility
- XP on MBR partiton 4.
- MacOSX is using GPT partitions 5 and 6.
- Ubuntu on partitions above 6, using grub boot on partition 2
- shared data on MBR partition 3 

You might even be able to improve the Wiki based on your experience.

---

