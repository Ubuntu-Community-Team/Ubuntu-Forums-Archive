---
title: "Trying to dual-boot with XP ..."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Murrquan on 2007-08-11
And I've run into a weird problem.

You see, I had to reinstall Windows, because I'm switching from pure Fedora 7 to an Ubuntu / XP dual-boot setup. Unfortunately, Windows does not want to start up, on account of an error message where it says that it cannot find \Windows\System32\hal.dll.

After a bit of research, I found that this was because the boot.ini file is trying to access XP on a partition I don't have it on. (See link: [http://www.kellys-korner-xp.com/xp_haldll_missing.htm]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm")) Unfortunately, I cannot access the boot.ini file to change it, because my system will not start up.

I have Live CDs for Ubuntu 7.04 as well as Fedora 7, but I'm not sure how to access the NTFS file partition to change the file. Is there any way I can do that? If if needs some downloadable program I could install Ubuntu and then grab it.

Am I on the right track? Help, please ^.^;

---

### Post by eapache on 2007-08-11
In ubuntu, install the NTFS Configuration Tool through Add/Remove, run it from Applications>System Tools, and enable it for internal and external drives. Then you should be able to find your disk under the Places menu.

---

### Post by jeremy1138 on 2007-08-11
> **Murrquan said:**
> And I've run into a weird problem.

You see, I had to reinstall Windows, because I'm switching from pure Fedora 7 to an Ubuntu / XP dual-boot setup. Unfortunately, Windows does not want to start up, on account of an error message where it says that it cannot find \Windows\System32\hal.dll.

After a bit of research, I found that this was because the boot.ini file is trying to access XP on a partition I don't have it on. (See link: [http://www.kellys-korner-xp.com/xp_haldll_missing.htm]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm")) Unfortunately, I cannot access the boot.ini file to change it, because my system will not start up.

I have Live CDs for Ubuntu 7.04 as well as Fedora 7, but I'm not sure how to access the NTFS file partition to change the file. Is there any way I can do that? If if needs some downloadable program I could install Ubuntu and then grab it.

Am I on the right track? Help, please ^.^;


Is the NTFS partition hidden?  I had a similar problem when I first set up my dual boot sytem.  I had to take my hard drive out of my computer and put it in an enclosure and then plug it in to another windows computer with Norton Partition Magic on it to unhide the partition.  After all that the computer ran perfectly!  I'm betting this is the trouble you're having.

---

### Post by Murrquan on 2007-08-11
Many thanks for the replies!

Unfortunately, I seem to have run into another problem ... Ubuntu is trying to install onto partition 1 and format it as EXT3, which is a bad thing because I think partition 1 is the NTFS partition I set up for XP. >.< I already used GParted in the Fedora 7 Live CD to partition the HDD, and I'd picked out the partitions for Ubuntu to use, but it doesn't seem to be giving me the options to select them.

It's letting me repartition the drive, but it doesn't list NTFS as an option -- just FAT32, which I think that's supposed to be more prone to fragmenting.

I think the problem is that I haven't actually installed Windows yet. The installer got as far as copying the files to my hard drive, then when it restarted it crashed as described above. So Ubuntu doesn't know that partition's supposed to be for Windows XP.

Right now I'm thinking it might work to use GParted to just turn the whole disk into an NTFS file structure, then install Windows XP, then install Ubuntu alongside it like it seems to be designed to do. Do you think that'd work? Once again, many thanks for the help.

---

### Post by jeremy1138 on 2007-08-11
> **Murrquan said:**
> Many thanks for the replies!

Unfortunately, I seem to have run into another problem ... Ubuntu is trying to install onto partition 1 and format it as EXT3, which is a bad thing because I think partition 1 is the NTFS partition I set up for XP. >.< I already used GParted in the Fedora 7 Live CD to partition the HDD, and I'd picked out the partitions for Ubuntu to use, but it doesn't seem to be giving me the options to select them.

It's letting me repartition the drive, but it doesn't list NTFS as an option -- just FAT32, which I think that's supposed to be more prone to fragmenting.

I think the problem is that I haven't actually installed Windows yet. The installer got as far as copying the files to my hard drive, then when it restarted it crashed as described above. So Ubuntu doesn't know that partition's supposed to be for Windows XP.

Right now I'm thinking it might work to use GParted to just turn the whole disk into an NTFS file structure, then install Windows XP, then install Ubuntu alongside it like it seems to be designed to do. Do you think that'd work? Once again, many thanks for the help.

This is exactly what I did for my dual boot laptop...  It worked without a hitch...  Aside from the fact that I installed boot magic as my boot loader like a big dummy!  Don't do that and you should be fine.

---

### Post by Murrquan on 2007-08-11
Worked like a charm ^.^ XP is up and running ... now I just need to install my games, and get Ubuntu to resize the partitions. Thanks, everyone!

---

