---
title: "Dual boot, adding windows?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by mojoman on 2006-08-23
Hi,

I'm planning to buy a new computer (:D ) and will be using Ubuntu on it (as I do on the laptop I now have) and it will be my primary, and probably only, OS on that computer.

However, if I later would like to add a Windows partition, is that at all possible?

I'm sorry if this question has already been answered. I've searched the forum but as far as I could tell all the threads, tips, and how-tos on dual boot all presupposed that Ubuntu was added to a Windows-box, not that Windows was added to a Ubuntu-box (and I seem to recall that Windows erases the entire HD on installation, or am I mistaken?).

Anyway, I probably won't need Windows at all and if I for some reason in the future would I'd rather add it then, as long as it does not entail erasing the entire HD. If that is required it might be a good idea to start with installing Windows and then partition the drive with the Ubuntu installation CD and install Ubuntu. If I later need the space rather than windows (which seem likely), I could just  delete the windows partition and add it to the Ubuntu system. Right or wrong? :-k 

Best regards
/Mojoman

---

### Post by annda on 2006-08-23
you can add windows later, no problem, just make sure you have a free disk partition for it (i thing gparted or even ubuntu livecd will let you prepare that).

then 1. install win, which will erase grub (the boot menu), and 2. insert the ubuntu live cd to reinstall grub.

you're set to go, no data lost.

---

### Post by Viral on 2006-08-23
I think it can be done, in fact, when I installed Windows XP From the disk, it asked me which partion to install Windows on. So I believe you can, I just wouldn't know how to setup a duelboot prompt after the BIOS loads.

---

### Post by Malac on 2006-08-23
Windows needs a primary partition to boot from and it helps if it is the first one on the drive.
So I would make a fat32 partition at the beginning of the drive which you can use for other files until you want to install Windows.
Just remember that Windows will write over the GRUB menu when it installs so you will need to either use the live cd to restore it or some other program which can save and write MBR. Or a grub boot floppy to boot into Ubuntu and restore GRUB from there.
There are plenty of explanations for how to do this on the forum.

---

### Post by Drakkor on 2006-08-23
If you think you're going to need Windows, it's a lot easier just installing Windows first,then Ubuntu for a dual-boot machine ! Even if you don't use Windows,like me...lol :mrgreen:

---

### Post by mojoman on 2006-08-23
> **annda said:**
> you can add windows later, no problem, just make sure you have a free disk partition for it (i thing gparted or even ubuntu livecd will let you prepare that).

then 1. install win, which will erase grub (the boot menu), and 2. insert the ubuntu live cd to reinstall grub.

you're set to go, no data lost.

Excellent! :p  There shouldn't be a problem to divide one of the existing partitions after the installation (for example, if I have a 100 GB /home partiton I could use gparted to shave of some 20 GB, convert it to NFTS and use that), right?

Good to know that I can start out with a clean system ;) 

Thanks
/Mojoman

---

