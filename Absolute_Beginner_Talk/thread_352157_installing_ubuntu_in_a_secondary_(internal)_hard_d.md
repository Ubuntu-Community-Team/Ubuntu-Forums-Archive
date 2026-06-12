---
title: "installing ubuntu in a secondary (internal) hard drive"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by preciousnightmare on 2007-02-02
I just bought a Maxtor ata internal hard drive 200gb (it also came with an installation software which can partition the hard drive) and I plan on using this as a secondary hard drive. So after I successfully connect it and configure my BIOS should I use the cd to partition it for ubuntu or just leave it as it is and just pop the ubuntu cd and let the ubuntu cd partition it?

---

### Post by OldTimeTech on 2007-02-02
ubuntu partions for itself better, but sometimes it has a difficult time with second drive.

If you go to search above and type in install to second drive.....because there has been many discussions about loading to second drives.

---

### Post by The Noble on 2007-02-02
Just pop in the ubuntu disc and have fun! Maxtor is just covering their bases with the disc, as most modern operating systems can do their own partitioning. Ubuntu will only touch the second hard drive with all of the system files, but it will install grub onto the master boot record on the first hard drive. Essentially, that provides you a way to boot into the second hard drive. Don't worry, everything will be fine.

---

### Post by adza on 2007-02-03
Hi there... i installed last night onto a second IDE drive for dual booting puproses.. i read this in a separate thread (can't seem to find it again to post the link - sorry!) but it was devilishly simple... steps as follows..

           1) open BIOS and set boot prioritry of HDD to your 2nd HDD first
           2) Install ubuntu off live cd to this drive, allowing installer to partition new drive
           3) Intallation will detect 2nd operating system and load GRUB boot loader
           4) when you reboot, GRUB will prompt you for which operating system...

   Worked a treat for me last night... i'm now a linux user! (and loving it)

---

### Post by Tiburon41 on 2007-02-03
I would let Ubuntu do all its own partitioning unless you use a program like Partition Magic.  Even then, Ubuntu, as others have said, does a very nice job all on it's own.  

When I did my install, I had already formatted (in FAT32) and loaded data on to my secondary drive (for video editing, etc), so I had to move and resize partitions to allow for unallocated space at the front of the drive.  If your new drive is clean, though, let Ubuntu do it all.

Good luck!

---

