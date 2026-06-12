---
title: "Please Help Me"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by CorranSW on 2007-04-01
Hi i have installed ubuntu 6.10 about several times over on my desktop and each time it has worked fine..... untill now..... I wiped my hdd a couple days ago and installed windows, then i installed ubuntu... well tryed to at least.... the boot menu comes up and give me a message saying 'unknown keyword in config file' something like that..... then i go to the menu were i get the option to install linux.... click on it... kernal opens up then i get a black screen with a flashing underscore that does not procide any further.... What now?

---

### Post by land0 on 2007-04-01
It sounds like the GRUB boot manager is borked. Reinstall Ubuntu and see if it happens again.

---

### Post by CorranSW on 2007-04-01
i cant install any operating systems..... even windows is getting the same error now i dont know what to do i just want a working OS now i dont care which one it is

---

### Post by land0 on 2007-04-01
Ok the master boot record is borked then not GRUB. Get a M$ win98 boot disk boot up the pc using it. Once at the command promt type **fdisk /mbr**. Then reinstall OS of choice. Go here for a boot cd iso [http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/Win98_bootdisk.iso](http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/Win98_bootdisk.iso) or for a .exe version [http://www.allbootdisks.com/downloads/Disks/Windows_98_Boot_Disk_Download49/Windows98_SE.exe](http://www.allbootdisks.com/downloads/Disks/Windows_98_Boot_Disk_Download49/Windows98_SE.exe)

---

