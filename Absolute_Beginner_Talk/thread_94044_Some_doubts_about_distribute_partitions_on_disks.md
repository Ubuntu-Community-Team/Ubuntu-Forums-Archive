---
title: "Some doubts about distribute partitions on disks"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by JuliusCaesar on 2005-11-23
Hi

First of all, sorry by my poor english.

I'm Ubuntu user but I need dual-boot WIN/LINUX in my home desktop, currently it is 5 years old (PIII -256 Mb) and I will substitute it in few days.
The desktop box has an 120 Gb IDE disk, parted (more or less) as shown:
ext3 5   Gb -> /boot
ext3 15  Gb -> /home
ext3 35  Gb -> /
SWAP 512 Mb 
vfat 35  Gb -> (shared)
NTFS 10  Gb -> (WinSystem) All win system directories, program files ...
NTFS 20  Gb -> (WinData) Users data.

The new box has a 200 Gb SATA disk but I will append the IDE one also. 
I have some doubts about the partitions and where mount each one.
I'm sure that SATA disk are faster than IDE, isn't it?, but due to my lack of knowledge in the matter, I have these questions:
How must I use them? I do not want dedicate one disk per each system. 
I am thinking about format the 'shared' partition in ext2/3 and access it from WIN using "Ext2 Installable File System For Windows" but... 
Where do I put it, in SATA disk or in IDE one? 
The same question about OS, which disk should I use to put 'winSystem', /boot' and '/'?

How could distribute partitions on the disks for optimal efficiency?
What do you suggest about? 
Would you use a different way to organize? (other partitioning mode for example)


P.S.

We have 2 users in both systems (OK, WIN uses ADMIN too).
We use Ubuntu for:
Proffesional matters:
- CAD (QCad)
- Office (OO.o writer, calc & draw)
- E-mail client
- Browser
- Documentatation (LyX)
Leisure
- Music player & storing (shared win/lin), CD ripper.
- Photo, basically storing (shared too) and slideshow creation (Cinelerra, DVDStyler).
- 3d (blender)
- C/C++ development (anjuta/glade).
Ubuntu mounts vfat (rw) and 'data NTFS' (r) partitions.

We use Windows because:
- Adobe Distiller, some colleages cannot modify my PDFs created using OOo.
- Some software for taxes is only for Windows.
- One of my mp3 players is only accesible by windows.
- C/C++ development (DevCpp + WxWidgets)
- Access to stored photos and music.

---

