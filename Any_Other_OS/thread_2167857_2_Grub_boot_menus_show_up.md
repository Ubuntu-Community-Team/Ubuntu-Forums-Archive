---
title: "2 Grub boot menus show up"
date: 2013-08-15
forum: Any Other OS
---

### Post by void2 on 2013-08-15
*_**I am really sorry if this is wrong forum,i am new.**_*

I recently installed Zorin OS side-by-side of Windows 7 and 8.Whenever i boot up 2 boot menus show.

Currently i use GRUB as my boot menu/loader.

Here is what i got when booting into FIRST menu:

[B]-Zorin OS
-Windows 8 Loader[/B]

And windows 7 is missing!

When i click on Windows 8 Loader,new boot menu loads,providing 2 entries:

[B]-Windows 7
-Windows 8.[/B]

So basically every time two boot menus appear.

_Is there any way to put all three OSes on first and remove other one?_

---

### Post by void2 on 2013-08-15
Anyone?I really need help!

---

### Post by pissedoffdude on 2013-08-15
In other words, you're first prompted by grub and selecting Windows 8 takes you to the Windows 8 graphical bootloader?  You're going to have to give us more info about your installation.
  
Are Windows 7 and 8 installed on the same hard drive but different partitions, or are they entirely separate hard drives?  If they're on separate hard drives, you can use EasyBCD to restore the boot sector of each hard drive, then just edit the boot.ini for Windows 8 and remove 7 and the boot.ini for 7 to remove 8 (if it even adds it).  Afterwards, reboot into Zorin and run a "sudo update-grub"

Edit: I also wanted to say DO NOT use EasyBCD to overwrite the MBR of the HDD Zorin is on, otherwise you won't have a grub menu.

---

### Post by oldfred on 2013-08-15
Windows with BIOS booting can only boot from one partition, or the active partition which we see as the boot flag.

If both installs of Windows are in primary partitions you can move boot flag and repair the partitions with  a Windows 7 repairCD and a Windows 8 repairCD or flash drive.

Discusses Vista, but all Windows in BIOS mode are the same.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

