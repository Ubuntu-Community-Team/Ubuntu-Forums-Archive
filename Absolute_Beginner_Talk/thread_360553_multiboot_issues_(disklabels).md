---
title: "multiboot issues (disklabels?)"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2007-02-13
Hi, I'm having an issue with setting up windows XP on a large hard disk.

I've now got myself a brand new, shiny, 250Gb hard disk (that's actually only 232Gb).  My intention is to reinstall Ubuntu as the primary operating system, as well as windows XP (for some astronomy programs I have), windows 98 and DOS (for old games).

I set up the partitions and formatted them using GParted, then ran windows setup - all it could see was a 127Gb drive, with one partition of 127Gb, which didn't correspond to any of the partitions I'd set up.  The only way to install windows is to let it create a new partition structure, using only the first 127Gb of the drive.  I can set it up this way, but the problem is, if I ever want to reinstall it, it's going to wipe out everything else on the drive as far as I can tell.

I can't find any reference to a limit of 127Gb with winXP (have tried google, with no success); could it be that I created the disklabel with GParted??  If so, is there a way to delete this and let the windows setup program create its own (if this might fix it).  I've used an MSDOS disklabel, so I doubt this is it, but that's the only thing I can think of.  Any help much appreciated.

PS. sorry if this should be in the 'other OS' forum, I wasn't sure whether it counted as an Ubuntu or Windows issue... I did think about it though :-)

---

### Post by igknighted on 2007-02-13
> **Big_Croc7 said:**
> Hi, I'm having an issue with setting up windows XP on a large hard disk.

I've now got myself a brand new, shiny, 250Gb hard disk (that's actually only 232Gb).  My intention is to reinstall Ubuntu as the primary operating system, as well as windows XP (for some astronomy programs I have), windows 98 and DOS (for old games).

I set up the partitions and formatted them using GParted, then ran windows setup - all it could see was a 127Gb drive, with one partition of 127Gb, which didn't correspond to any of the partitions I'd set up.  The only way to install windows is to let it create a new partition structure, using only the first 127Gb of the drive.  I can set it up this way, but the problem is, if I ever want to reinstall it, it's going to wipe out everything else on the drive as far as I can tell.

I can't find any reference to a limit of 127Gb with winXP (have tried google, with no success); could it be that I created the disklabel with GParted??  If so, is there a way to delete this and let the windows setup program create its own (if this might fix it).  I've used an MSDOS disklabel, so I doubt this is it, but that's the only thing I can think of.  Any help much appreciated.

PS. sorry if this should be in the 'other OS' forum, I wasn't sure whether it counted as an Ubuntu or Windows issue... I did think about it though :-)

If you just got a brand new HD, why not leave both in there?  You could put windows on the one it is familiar with and linux on the new one, and use the rest of the space as a shared ext3 partition for files you want to access in Ubuntu and MS.  This would also leave your MBR in tact for both, so if Ubuntu went down, you could change the order of disks to boot from and still have windows, no worries about grub over-writing it.

---

### Post by Big_Croc7 on 2007-02-13
Windows dosen't like the old drive! I don't know why; it ran fine on the system when it was installed on an old 4Gb drive, but when I installed it on my present 60Gb drive it would barely run for 10 mins before crashing.  (Strangely, Ubuntu runs fine on the 60Gb disk.)  I tried reinstalling windows twice on the 60Gb disk and it wouldn't even complete setup.  I don't have a working install of windows at all at the moment, and I thought I may as well reinstall Ubuntu as well on the faster disk.

---

### Post by igknighted on 2007-02-13
> **Big_Croc7 said:**
> Windows dosen't like the old drive! I don't know why; it ran fine on the system when it was installed on an old 4Gb drive, but when I installed it on my present 60Gb drive it would barely run for 10 mins before crashing.  (Strangely, Ubuntu runs fine on the 60Gb disk.)  I tried reinstalling windows twice on the 60Gb disk and it wouldn't even complete setup.  I don't have a working install of windows at all at the moment, and I thought I may as well reinstall Ubuntu as well on the faster disk.

What kinds of disks are they (IDE or SATA?).  Sometimes windows needs drivers loaded during the install for various components, so this might be your issue (further debunking the myth that a linux install is harder than a windows one).  Also, what do you need windows for?  If it isn't for games or other 3D programs, try using VMWare or some other virtualization... you can run windows in Ubuntu at basically native speeds, with no need to reboot,  Plus there is no issue with partitioning or any of that nonsense.

---

### Post by Big_Croc7 on 2007-02-13
They're all IDE drives.  I don't *think* it's a driver issue - Windows used to run ok, except it would hang at seemingly random points (usually about 10 mins apart); when I tried running setup again the last two times, it hung at different points during setup - complete system hang, no mouse movement, ctrl-alt-del not working.  I'd have thought it was the power supply or something playing up, except Ubuntu worked fine :confused: 
Looks like I might just go with VMWare (I naively thought it would be easier to get a dual-boot system working!), though I tried running the old classic Transport Tycoon in DOSbox and it was a bit slow and juddery.

My idea was, to install xp, then Ubuntu (as that's what's recommended) then, later, win98 + dos (that has to be later as I don't have the disks at present), but even if I get xp + ubuntu working, it looks like 98 might mess it up.

---

### Post by Big_Croc7 on 2007-02-14
It looks like I have more of a problem than I first thought.  I decided to ignore windows for now and install Kubuntu Edgy on the new 250Gb disk (as a slave, leaving my dapper install on the 60Gb as master).  The install went fine (except that it reported different numbers for the partitions on the 60Gb in QTparted and the installer), but grub won't load Kubuntu.  It gives me an error 15 - file not found when I try to boot the 6.10 entry.  I've also tried adding lines to my old grub (on the 60Gb) to boot the new install, but I get errors 18 and 21.  It seems like it might be a problem with the bios not recognising the drive correctly, except that a Live CD can read and write to the whole 250Gb disk fine (using dapper, edgy and a very old knoppix live cd).

Any help here? I'm stumped! :confused:

---

### Post by Big_Croc7 on 2007-02-14
Ok, after testing it, I've found that the following things don't work with my 250Gb drive:

1. booting anything with grub
2. installing windows beyond 131Gb

These however work:

1. installing Ubuntu (anywhere on the drive)
2. installing windows to the first 131Gb of the drive
3. running windows using windows bootloader
4. acessing the drive from a live CD; editing partitions with GParted or QTParted
5. installing grub to the MBR

booting anything on this drive with grub fails, whether grub is installed on the same drive or another one.  Suggestions?

EDIT: oops, just realised maybe I should have edited rather than multi-posting; sorry!

---

