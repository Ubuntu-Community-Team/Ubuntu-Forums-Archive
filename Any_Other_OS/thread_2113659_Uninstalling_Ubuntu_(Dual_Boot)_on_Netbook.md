---
title: "Uninstalling Ubuntu (Dual Boot) on Netbook"
date: 2013-02-08
forum: Any Other OS
---

### Post by sampark1995 on 2013-02-08
Hello, I have recently installed Ubuntu as a dual boot OS on my Samsung N150P netbook. After testing it out for a bit, I realized that the OS is simply too much for my netbook to handle. 


Thus, I would like to remove it.
However, after some research, I've learned that the only way to remove it safely is by using a recovery CD.

The only problem is, my netbook doesn't have a CD drive.
What should I do?

Thanks.

---

### Post by oldfred on 2013-02-08
Welcome to the forums.

You can install  this into the flash drive you used to install Ubuntu.

       An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

    
You should always have a repairCD or flash drive for the current version of every operating system you have installed.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by sampark1995 on 2013-02-08
Thank you so much!
Now that I've used OS-uninstaller, do I just remove the partitions from my Windows?

---

### Post by oldfred on 2013-02-08
Yes.

While you can use gparted on liveCD to delete Linux partition. Only use Windows to expand the NTFS partition and reboot. Windows has to run chkdsk and make other repairs on any partition resize. Or with gparted make the space another NTFS data partition which then would be a d: drive.

Moved to Other OS since Windows issues.

---

### Post by AMKawam on 2013-02-08
You can delete the linux partition completely, format the free disk space as NTFS. You can use a partitioning tool for windows to re-partition your drive if you don't like to have too many NTFS partitions.

---

