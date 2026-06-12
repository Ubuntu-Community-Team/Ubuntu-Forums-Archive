---
title: "Installation on ppc"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by mdd5148 on 2007-01-04
I am trying to install Ubuntu on my 1.67 G4 powerbook ppc.  I did not want to loose data so I have shrunk the OS X partition and created a new partition using iPartition.  Currently both of these paritions are supposedly HFS (Mac OS/Mac OS Extended) <-- Could this be the problem?

When I run through the installer I get to the point that asks to select a disk.  My two options are to erase entire disk or manually edit partition table.  As previously stated I don't want to reformat the OSX partition so I have been selecting manually edit partition table.  The installer however then shows my hard drive as one unallocated block.  I can select this and continue to the next page and select mounting points, however I cannot continue beyond that screen as the  forward option is un-available.

The very first time I ran through the installer the hard drive was detected as seperate blocks but I was still unable to go past the mounting point screen.

I have tried the following:  using iPartition to create both one big and two seperate partitions after the OSX partition (install and swap), moving the OSX block back and putting desired linux partition infront of OSX in hopes that the installer would detect it (no dice), and have even tried creating two partions using the format linux ext2 and linux swap provided in iPartition.

Any help would be greatly appreciated. :-k

---

### Post by Tenicus on 2007-01-04
You should have 
the HSF partition
A 1GB swap partition
and an ext3 partition

I dont know why you see it as one block and not seperate partitions.
Use Disk Utility to erase the other partitions (NOT the OSX one) and leave them as free space.  Dont format the freespace
THEN try installing.

---

