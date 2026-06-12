---
title: "Help with making a bootable windows 7 installation usb drive from ubuntu 12.04"
date: 2012-08-05
forum: Any Other OS
---

### Post by Free Radical on 2012-08-05
Got a program called "WinUSB". keep getting the same error code:
"Installation failed! 
Exit code:256
Log: formatting device... 
error: can't have a partition outside the disk!"

I have a windows 7 iso and I'm trying to put it onto a usb flash drive to install it. can I get a step by step guide to doing it from terminal? I figure I can just set a partition to active bootable and then it will be simple if I just drag and drop the files.

---

### Post by oldfred on 2012-08-05
Moved to otherOS.

You cannot just make a partition bootable to have it boot. Windows has boot code in the MBR that then calls the code in the partition boot sector PBR that has the boot flag. The flag just tells the MBR which PBR to go for more boot info.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I tried creating a Windows repair disk from Ubuntu and never got it to work. I was able to burn the repair ISO to a CD and then use the CD to copy itself using Windows commands to create the USB. That created the bootable partition and it was just copying files.

Supposedly from a separate partition on hard drive.
Use unetbootin to copy windows iso to partition and install:
[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)

Create Windows 7 USB 
[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)
[http://www.boot-land.net/forums/index.php?showtopic=8944](http://www.boot-land.net/forums/index.php?showtopic=8944)
Windows 7 repair CD
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by jnedenrod on 2012-08-05
I used NetBootIn for a flash drive. It's quick and painless.  Be sure you're not installing it on a public computer as its security settings could prevent a successful install.  "Partition outside the disk" makes it sound like a disk space issue.  Are you sure there's enough space on your flash drive for the install?

---

