---
title: "Format external hard drive to work with XP and Ub?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by jammadave on 2007-09-07
Once I get Ubuntu running....

Let's say I want to write all my media files to an external HDD with WinXP, and read them back in Ubuntu - how would I do such a thing?   Is it just a matter of making sure the HDD is formatted NTFS?

Thanks!
Dave

Still no luck getting ubuntu to load all the way to the desktop, though =0(

---

### Post by dca on 2007-09-07
Nine times out of ten, any external HDD(s) I get whether USB thumbdrive or actual external MyBook or whatever I format NTFS for fear of having it used all over the place...

---

### Post by justleen on 2007-09-07
FAT32 is an option.. is nativly supported by both OS'es.. but it has a 4GB file limit, which can be anoying..
Other options:  format as EXT3, and use the EXT3 driver for windows
or
format as NTFS, and use the ntfs-3g (drivers and tool) to use under linux

---

### Post by jammadave on 2007-09-07
OK, so with either NTFS or EXT3, there are ways of being able to just use it on any machine I may happen to attach it to in my travels?

---

### Post by vanadium on 2007-09-07
For compatibility during travelling, FAT32 is the one best option: works on Linux, Mac, any flavour of windows (Me, XP, ...)

---

### Post by Hospadar on 2007-09-07
I would suggest NTFS with the ntfs-3g drivers, I've had a good experience with these drivers and their companion tool ntfs-config.  Plus I would guess that if you plug it into another machine that is not yours, that machine will be a windows machine, so NTFS will probably be easier.

---

### Post by jammadave on 2007-09-07
Hospadar, that's what I was thinking.

But vanadium, FAT32 automatically works?    Would a ripped DVD movie come in at under 4GB?  That's about the biggest thing I can imagine having stored.

---

### Post by adamklempner on 2007-09-07
As long it is not raw video, it should fit.  I don't have any ripped movies to check, but I imagine that a compressed divx file will probably be ~1GB.

My external hard drives are both FAT32.  It is the safest bet provided that you don't have 4+ GB files.  I tried the linux NTFS drivers a while ago and had lots of problems.  Granted it is probably better now, but I know that FAT32 just works no matter where you go.

---

### Post by dca on 2007-09-07
Be careful w/ FAT32, though.  The blocks are larger.  I use 100GB - 400GB externals for backing up user data (laptop users) where I consult.  If they all have 80GB laptop HDDs and you try mass copying large files you'll get disk full errors because it mathematically magically computates the size during file migration based on the block sizes...

---

### Post by vanadium on 2007-09-07
> 
being able to just use it on any machine I may happen to attach it to in my travels?


For this requirement there is only one answer. fat32 can be read without having to install drivers by most Windows flavours, macs (I think) and Linux. However, with FAT32, you cannot store +4Gbyte files, so ripping a DVD as a single ISO is not possible.

If you need to write +4GByte files, you will need ext3 or ntfs at the cost of compatibility. ntfs is read by a majority of computers out there (since Windows remains the most widely used OS), it is read by most Linux systems (but not written to unless you install ntfs-3g) and for Apple, you probably need drivers even to read ntfs (someone correct me if this is wrong). As already mentioned, with additional software, you can make Windows read ntfs (don know at all for Apple).

---

### Post by stchman on 2007-09-07
> **jammadave said:**
> Once I get Ubuntu running....

Let's say I want to write all my media files to an external HDD with WinXP, and read them back in Ubuntu - how would I do such a thing?   Is it just a matter of making sure the HDD is formatted NTFS?

Thanks!
Dave

Still no luck getting ubuntu to load all the way to the desktop, though =0(

Use FAT32 for external devices.

---

