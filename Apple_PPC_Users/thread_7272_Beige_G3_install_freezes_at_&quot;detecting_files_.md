---
title: "Beige G3: install freezes at &quot;detecting files system&quot;"
date: 2004-12-05
forum: Apple PPC Users
---

### Post by xico on 2004-12-05
Hello all,
The install invariably freezes at the action "detecting files system..." under the screen "Starting partitionning tool" (76% of it).
Do you have any idea of what's going on?

My config:
Beige G3 MT 266/640/2x4,5  
first disk for OS9.2.2 and the second for Ubuntu (unmounted in OS9) partitionned as:
1 Apple_UNIX_SRV2 swap   (960M)
2 Apple_UNIX_SRV2 ext3    (3,3G)
3 Apple_partition_map Apple
4 Apple_Driver43*Macintosh
5 Apple_Driver43*Macintosh
This disk has not been formatted after partitionning. This is normal as there is no HFS partition, right?

Graphic cards: Rage II on motherboard and IMS tt 3D on slot.
BootX as bootloader

Thanks for your answers

François

---

### Post by bcb on 2004-12-05
I think it's a partioning issue, but not sure why.

1) To boot your Beige you will need an HFS partition.  Old World macs need to use either BootX (needs a full System Folder, since it's just a control panel) or miBoot (uses a greatly reduced System and Finder in a minimal System Folder), which must reside within the first 8 G of the harddrive.

2)  How'd you partition it in the first place?  The best way is to use a MacOS CD.  Using drive setup just create 2 partitions:  the first will hold the System Folder needed to (partially) boot the machine, the second can be the remaining space.  In the installer, use the partioner to delete the second partition.

Good luck, it should work.  Read up on how to use BootX (it's the normal Old World boot method), and also the Old World PPC howto  over at [www.ubuntulinux.org](www.ubuntulinux.org)

---

### Post by xico on 2004-12-06
Thank you for your answer but I think you didn't understand well my question: 
I use two different physical disks, one with OS9,BootX.... and one for ubuntu that I partitioned all the possible ways (Drive setup with 1, 2, HFS, Unixlike..., pdisk with swap, ext3,...). None of the two physical disks is recognized by the Ubuntu partition tool...
I'm already in the Install process that I reached with BootX, but I get stuck at file syst recognition

Any idea?

Thanks for answers

Francois

---

### Post by ktindle on 2004-12-12
What interface is being used for these drives?  (IDE vs. SCSI)

The second drive should be set up in Apple Drive Setup for the
entire drive as "Unallocated."  The Ubuntu installer will allow
you to make the ext3 and swap partitions in Manual mode.

Many beige G3's cannot use a second IDE HDD, and so you
must add the second drive as SCSI and drop to the second
virtual console in the installer and do a "modprobe mesh".
This lets the installer find the second drive.

---

### Post by xico on 2004-12-14
Thank you for your answers,
Both of my disks are scsi.
I solved the problem by setting the Ubuntu drive as master.
It doesn't work yet but I've been able to perform the first part of the install.

Francois

---

