---
title: "Creating a Windows live USB"
date: 2012-10-26
forum: Any Other OS
---

### Post by Jimstehrman on 2012-10-26
Hey all,

I'm having some trouble creating a windows live usb, the following lists the methods I've tried and the problems I encountered with each. For all I have an already NTFS formatted (and working) 8 Gb usb stick.
Unetbootin - Windows 7 requires an NTFS formatted stick to be able to correctly operate. However Unetbootin has recently removed support for NTFS usb drives, that is it will not recognize it. I've heard that older versions do have this functionality, however the versions 460 and 506 that I have tried have depended on something called LibXrandr.so.2, which looks to be unavailable to Ubuntu 12.10.

Extracting to drive using archive manager - When I open the .iso with the archive manager, it comes up with one file called "." that contains nothing. Trying to extract it yields one file called README.txt with 0 bytes of data.

Copying files from mounted iso - when I mount the .iso and try to copy the files over to my stick I get "Error splicing file: Input/output error" on such files as "bootsec.exe.mui" I can choose to ignore it and it copies over some of the files.

It seems there is no "easy" way for me now, however some insight into these issues would be really appreciated if anyone has something to offer!

Thanks!

---

### Post by oldfred on 2012-10-26
You cannot create a Windows liveCD like you can with Ubuntu. Windows is licensed for only one PC and embeds info on that PC. It also knows if drive is not permanently installed and will not boot from removeable drives.

You can make a repair flash USB. These only run the repair console.

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by qamelian on 2012-10-26
> **oldfred said:**
> You cannot create a Windows liveCD like you can with Ubuntu. Windows is licensed for only one PC and embeds info on that PC. It also knows if drive is not permanently installed and will not boot from removeable drives.

Actually, you *can* create a bootable Windows Live CD. I use them all the time at my day job. A quick search on Google will find a few methods. At work we use a tool from Activ@ to create the bootable thumb drive containing a minimal Windows environment that we use for imaging PCs and running some diagnostic tools.

---

### Post by lisati on 2012-10-26
In both Windows and Linux, a filename of "." has a special meaning, and usually refers to the current working directory.

---

