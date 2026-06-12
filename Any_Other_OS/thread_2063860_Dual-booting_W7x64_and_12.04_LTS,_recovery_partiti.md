---
title: "Dual-booting W7x64 and 12.04 LTS, recovery partition broken"
date: 2012-09-28
forum: Any Other OS
---

### Post by hmmwhatsthisdo on 2012-09-28
So, I just installed Ubuntu 12.04 onto my laptop and I'm now using GRUB to load Windows 7. However, booting into Windows 7's recovery partition through GRUB causes an error to occur. I get a screen similar to that of the boot options menu, with the following text:

> Windows Boot Manager

[...]

File: \Boot\BCD

Status: 0xc0000034

Info: An error occurred while attempting to read the boot configuration data.


Once again, Windows 7 boots JUST FINE. However, the recovery partition appears to be broken at the moment. I'd like to have it so that I can boot directly into recovery mode from GRUB.

What should I do?

---

### Post by oldfred on 2012-09-28
What recovery partition?

Your vendor provides a recovery partition, which is just an image of hard drive as purchased. It will not install Windows, but just reimages/erases drive and makes it like it was on the day you bought it.

Windows often calls its 100MB boot/repair partition a recovery partition also. Using f8 you get to the Windows recovery or repair console. From grub menu you have to press f8 almost at exactly the same time as the Windows entry to get to the repair screens. Often better just to make a repairCD or USB.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by hmmwhatsthisdo on 2012-09-29
I mean Windows' recovery partition. I can see it in a partition manager like GParted or Windows' built-in one, but booting to it through the F8 menu or GRUB/BURG causes it to fail.

---

### Post by oldfred on 2012-09-29
Moved to Other OS as Windows issues.

I do not know a lot about Windows 7. I usually suggest using the Windows repairCD that they want you to make as soon as you purchased system.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)


Then you can run chkdsk and it sound like the BCD has errors and you may need to repair that. 

Normally Windows boots thru the 100MB boot/repair partition and grub just chain loads to that partition. Or did you copy bootmgr & BCD to main install?

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by hmmwhatsthisdo on 2012-09-29
I have a W7 Install disc (which comes preloaded with all repair tools a repair disc has), but I only have access to it when I'm at home.

That being said, how might I go about fixing this?

---

