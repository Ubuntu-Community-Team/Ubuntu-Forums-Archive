---
title: "Help repairing xp on triple boot setup!!!"
date: 2012-06-04
forum: Any Other OS
---

### Post by chronictoker on 2012-06-04
Windows 7, Windows XP, and Ubuntu 11.10 on triple boot.  My xp seems to be infected and I want to reinstall windows xp without destroying the boot loaders. Anyone's help would be appreciated :KS

I dont want to format anything, I just want to install over current file system.

---

### Post by Dapilot1 on 2012-06-04
Wouldn't you want to format your XP and start clean if it is infected? That is what I would do.

Just install XP onto the right partition and boot a live cd after.
Then [update grub]("https://help.ubuntu.com/community/Grub2/Installing") so XP doesn't steal your machine.

---

### Post by oldfred on 2012-06-04
Moved to other OS.

You have to be careful as Windows 7 may have moved all its boot files into the XP partition.

Windows only boots from the boot flagged or active partition. So second installs of Windows boot from that same active partition and literally move all boot file to that partition. You may be able to repair the Windows 7 partition if it is a primary partition.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

If you can boot into 7 be sure to create a repairCD or USB.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

