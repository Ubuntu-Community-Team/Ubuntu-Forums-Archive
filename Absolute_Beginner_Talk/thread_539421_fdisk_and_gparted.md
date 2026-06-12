---
title: "fdisk and gparted"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-08-31
I dont get the way linux partitions disks. In windows it was relitevely simple but there seems to be no logic behind fdisk or gnome partition editor.

When using gparted, i deleted my ntfs partition and created 2 linux ones. then formatted them. Fdisk however cannot see these as a print/verify says theyre is no partitions and that all the sectors are unallocated.

Then later, i tried again from scratch to get just one partition. Just using fdisk to create primary partition. Now theres a problem as i have a partition called /dev/&#347;dd1p1 mentioned in the partition list which seems right, as it is the only one required.
Problem is, when it mounts , i now have two drives, even though the fdisk program says i have only one.

How do i simply create a single primary partition (1 disk) and format it to ntfs?

---

### Post by jombeewoof on 2007-08-31
this shouldn't be that hard. 
what do you get when you 

fdisk -l

---

### Post by dgrafix on 2007-08-31
Device ...........Boot.......Start .......End........Blocks  ....Id  System
/dev/sdd1p1..................1.............11749.... 94373811   83  Linux
but when it hets hotplugged, 2 drives appear one 16gb and one 430gb :confused:


when i did it with gparted though (before) fdisk reported:
Device ...........Boot.......Start .......End........Blocks  ....Id  System
(nothing)
but there was obviously a partition there as i had files on it and could mount the disk


Do fdisk and gparted use different standards or siomething (i thought gparted was just a frontend for fdisk)

---

### Post by DLinn on 2007-08-31
Some Info-

This is from the respective man pages for Ubuntu 7.04.

gparted manual page:  GNOME frontend for parted.
gparted uses libparted to detect and manipulate devices and partition tables.

fdisk manual page:  Partition table manipulator for Linux.
fdisk (in the first form of invocation) is a menu driven program for creation and manipulation of partition tables.  It understands DOS type partition tables and BSD or SUN type disklabels.  There are several *fdisk programs around.  Each has its problems and strengths.  Try them in the order cfdisk, fdisk, sfdisk. (Indeed, cfdisk is a beautiful program that has strict requirements on the partition tables it accepts, and produces high quality partition tables. Use it if you can. fdisk is a buggy program that does fuzzy things - usually it happens to produce reasonable results. Its single advantage is that it has some support for BSD disk labels and other non-DOS partition tables. Avoid it if you can.  sfdisk is for hackers only - the user interface is terrible, but it is more correct than fdisk and more powerful than both fdisk and cfdisk.  Moreover, it can be used noninteractively.)

These days there also is parted.  The cfdisk interface is nicer, but parted does much more: it not only resizes partitions, but also the filesystems that live in them.

So gparted is a partition manipulator and fdisk manipulates and creates partitions.

This may only clear things up to the point of mud. But I've found that using these different programs is the best way to get the results you want.   :-)

---

