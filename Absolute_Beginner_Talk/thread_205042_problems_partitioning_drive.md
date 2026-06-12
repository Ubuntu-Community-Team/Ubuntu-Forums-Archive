---
title: "problems partitioning drive"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Siamese Dream on 2006-06-27
system: 
Toshiba Satellite 5105-S501 laptop
WinXP SP2
Intel P4 1.7Ghz
512 MB RAM
HD: TOSHIBA MK4019GAX 37.26GB

I get the live cd to boot and when I start the install I run into problems in the partitioning phase. I tried to do the automatic partitioning and it gave me an error. I tried to do the manual partitioning and it showed a lock next to my hard disk and I when I try to partition it says I do not have permission to access the drive? I am trying to run a dual boot between linux and WinXP.and I have 14.31 GB of free space. Any recommendations?

Thanks

---

### Post by LoDgEr on 2006-06-27
You should try freeing up another 10 GB.

---

### Post by verbatim210 on 2006-06-27
...and DONT use the live cd as an installation source

download the desktop/server/alternate and install from there

---

### Post by skale on 2006-06-27
you should 
a. defragment the drive
b. use the Windows XP cd to create/cut the windows partition (in FAT32 preferrably, you cannot write files to NTFS from ubuntu) and leave space unpartitioned for the swap and ext3(linux) You might want to backup everything, as changing to FAT32 would erase everything I think.
c. use the ubuntu alternate CD to install ubuntu and create an ext3 and swap partition(1.5GB max) in the unpartitioned space. 
d. the windows FA32 partition mounted automatically for me to /media/hda1/

Good Luck!
google "illustrated dual-boot" and pick the first one for help.

edit: your computer is almost like mine, except mines Dell. I put 30GB as FAT32, 8.5 as ext3 and 1.5 as swap.

---

