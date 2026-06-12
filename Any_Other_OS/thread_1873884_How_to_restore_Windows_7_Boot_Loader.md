---
title: "How to restore Windows 7 Boot Loader?"
date: 2011-11-02
forum: Any Other OS
---

### Post by snarfel on 2011-11-02
So I installed Ubuntu 11.10 today within Windows 7 which had about 55GB free on it's partition. However, when I booted into Ubuntu I started installing drivers and it said the memory ran out which is ridiculous. So I booted into Windows and deleted C:\Ubuntu and rebooted only to find that the boot loader had been wiped along with it. So right now, I'm using Ubuntu off my flash drive I originally installed of it, afraid to format or install another copy lest it write over my Windows copy. Is there an easy way to restore the Windows 7 boot loader if  you don't have the disks (I'm away from home at college). Or should I try to install Ubuntu again on the hard disk WITHOUT wiping it and somehow restoring the Windows boot loader from there? I really want to be able to boot into Windows again to do work... :(

EDIT: Tried the options 'Uninstall 11.10 and reinstall' and 'Replace 11.10 with 11.10'. Both said during the installation process that I didn't have enough memory...

---

### Post by CerberusCommand on 2011-11-02
Have you tried doing a google search? There's a forum for windows seven which has instructions on how to reset windows 7 MBR - [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by nothingspecial on 2011-11-02
Moved to Other OS/Distro Talk.

---

### Post by rng on 2011-11-02
Try this: 
- boot computer with flash drive
- when you get grub menu, press 'c' to enter command line mode
- enter following commands (pressing ENTER after each command): 
       > set root=(hd0,1)
       > chainloader +1
       > boot

See if it works and boots windows. It should if only mbr is corrupted and windows partition is all right.

---

### Post by Mark Phelps on 2011-11-02
There are a couple of different solutions you can try.

First, there is something called Boot Repair.  You download the image, burn it to CD, boot from that -- and are supposed to then be able to repair Windows boot.  Link is here:  

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Second, there is the Win7 Repair CD.  You go to the link below, purchase the proper image for your machine, download the image, burn it to CD, and boot from it:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

When you boot from it, select Repair and run Startup Repair at least three times.  That will restore Win7 boot.

---

### Post by mips on 2011-11-02
Boot off the Win7 dvd/install media and select REPAIR, and then do a FIXMBR.

---

### Post by oldfred on 2011-11-02
Above posts are good suggestions, but if you have to do a quick fix from Ubutnu you can use lilo. But best to create Windows repairCD also.

From Ubuntu you can install a boot loader that boots windows directly. Windows MBR only checks for active partition (boot flag) and jumps to that PBR partition boot sector to continue booting. Lilo does the same thing.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by snarfel on 2011-11-02
Yeah, I ended up being able to temporarily borrow a Windows disk from our campuses IT office and ran "bootrec /fixmbr" which resolved the issue. 

Before I mark it as resolved though, is there any reason why it would say memory low (less than 15mb) on Ubuntu and fail to install things yet on the very same partition, Windows said I had about 44GB free and how I can fix that issue? I might just end up partitioning off 100gb off my 1tb external and installing it on there so it doesn't interfere with Windows as much...

---

### Post by oldfred on 2011-11-02
Did you do a wubi install. That is just a file inside the NTFS partition.

Or how large did you make your / (root) partition.

From terminal:

df -H

---

### Post by rmayer32 on 2011-11-02
bootrec /fixmbr does the job long as you have the media to boot up too.

---

### Post by ChrisNelson790 on 2013-01-14
Hey, Although I am new to this forum as of course I am new to Ubuntu, I did go through MBR issues.

However I used EasyBCD to edit my MBR and it happens to fix the MBR issue. Hope it fixes your issue. If you do come across another way of fixing it, do let me know.

Cheers

---

### Post by coffeecat on 2013-01-14
Old thread closed.

---

