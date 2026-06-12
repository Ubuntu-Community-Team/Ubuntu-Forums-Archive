---
title: "Grub2 loading Reserved Partition on Dual Boot setup"
date: 2014-01-25
forum: Any Other OS
---

### Post by manuleka on 2014-01-25
I have installed Linux Mint 16 KDE alongside Windows 7 on a single 750GB HDD

When i select Windows on boot up i get an error message on a black screen... Grub is trying to load Windows from the reserved partition sda1 while Windows 7 is actually on partition sda2

can someone advice me or point me an easy way for a Linux illiterate on how to point Windows selection to the write partition on grub?

cheers

---

### Post by oldfred on 2014-01-25
Windows 7 installs normally to a 100MB boot partition on sda1 and the main install in sda2. 
So the boot files are in sda1. 

Did you resize Windows from Windows or the install. Windows always needs chkdsk after a NTFS partition resize. Often you cannot get to the repair console with f8 from grub as it is too quick. Some hit f8 at same time of enter in grub menu and make it work. But usually you need a separate Windows repairCD or flash drive.

 f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)


       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by manuleka on 2014-01-25
> **oldfred said:**
> Windows 7 installs normally to a 100MB boot partition on sda1 and the main install in sda2. 
So the boot files are in sda1. 

Did you resize Windows from Windows or the install. Windows always needs chkdsk after a NTFS partition resize. Often you cannot get to the repair console with f8 from grub as it is too quick. Some hit f8 at same time of enter in grub menu and make it work. But usually you need a separate Windows repairCD or flash drive.

 f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)


       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Linux was installed into a readily separate partition...

thanks

---

### Post by manuleka on 2014-01-30
I have diverted to Elementary OS Luna x64, Windows boot perfectly fine...

---

