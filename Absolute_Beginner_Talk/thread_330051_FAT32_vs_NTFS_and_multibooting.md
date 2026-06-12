---
title: "FAT32 vs NTFS and multibooting"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by teknoPunk on 2007-01-02
I would like to setup a multi-boot system with the following OS's:

98SE

XP Pro

Ubuntu

I know in the case of 98 and XP, 98 has to be installed FIRST.  In the case of Ubuntu should it be installed last and, if so, can Ubuntu's boot manager handle multi-booting the above OS's or should I use something like PowerQuest's BootMagic?

While I plan on having 3 system partitions, I also plan on having a shared partition for misc data files to share between the three OS's.  Is my best bet making this shared partition FAT32 for compatibility?  

I know it is possible to read/write to NTFS partitions with Ubuntu, however will I save myself a lot of hassle by just using FAT32?  (I know 98 won't be able to see the NTFS partition, but i'm not too concerned about 98 ).  Outside of security will I see much benefit by making my storage partition NTFS?

Thanks!

---

### Post by mxrten on 2007-01-02
Grub, which is installed by ubuntu, should have no problem booting the 3 OS's.

A shared FAT32-partition sounds like a good idea. I don't know how far the linux support for ntfs has progressed.

---

### Post by earobinson on 2007-01-02
> **teknoPunk said:**
> I know in the case of 98 and XP, 98 has to be installed FIRST.  In the case of Ubuntu should it be installed lastYes
> **teknoPunk said:**
> can Ubuntu's boot manager handle multi-booting the above OS's or should I use something like PowerQuest's BootMagic?Ubuntus boot manager (grub) can do it!
> **teknoPunk said:**
> While I plan on having 3 system partitions, I also plan on having a shared partition for misc data files to share between the three OS's.  Is my best bet making this shared partition FAT32 for compatibility?Yes
> **teknoPunk said:**
> I know it is possible to read/write to NTFS partitions with Ubuntu, however will I save myself a lot of hassle by just using FAT32?  (I know 98 won't be able to see the NTFS partition, but i'm not too concerned about 98 ).  Outside of security will I see much benefit by making my storage partition NTFS?
 Ubuntu can read and write ntfs for more info check this out [http://www.ubuntuforums.org/showthread.php?t=330038](http://www.ubuntuforums.org/showthread.php?t=330038), but im not sure about performance or 98
> **teknoPunk said:**
> Thanks!NP

---

### Post by justin_c18 on 2007-01-14
I have a Dual boot, with ext3, and nfts file systems. FS-Driver is installed on my ntfs partition which reading works perfectly, I can't write, but there's no use really, for me anyway. Since I use Ubuntu as my main OS.

[http://www.fs-driver.org/]("http://www.fs-driver.org/")
Figured I'd say something, 
Justin

---

### Post by bigken on 2007-01-14
you should have no problems as I see 

win 98 1st 

win xp 2nd

last ubuntu

for the easiest shared partition would be fat32 but remember its limitations of 2 gig file size 

if I were you I would use gparted liveCD to make my partitions

---

