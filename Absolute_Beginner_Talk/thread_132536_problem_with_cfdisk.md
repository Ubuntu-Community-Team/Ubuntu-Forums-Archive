---
title: "problem with cfdisk"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by nixclusive on 2006-02-18
[size=1]Problem straight down > [/size]

I have a 40 G hard drive out of which almost 33 G is full of multimedia! The leftover was dedicated for the Windows XP installation I had. I tried Ubuntu live CD (5.04) and decided to give it a try.

For that matter I booted into DOS using an old Win98 bootdisk and *deleted* my Windows Partitions using Partition Magic 8. hehehe 

I used to think that installing Windows is a breeze till I saw how Ubuntu installation worked. Honestly...swept me away. 

After deleting the Windows Partitions I resized the extended partition to make way for two Ubuntu partitions (/ and swap). I think linux handles primary/logical paradox (?) far better. 

[size=4]Now the problem:[/size]
when I tun cfdisk from the terminal I get this:

   FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap


What exactly is this? When I tried to run Partition Magic from Win98 bootable it gave me some Partition #??? error (I don't remember the no. maybe #114.)

What must have gone wrong? I can still access the data on the logical partitions but I'm not able to access the Partition Table any more :(

Screenshot:
[http://i5.photobucket.com/albums/y165/nixclusive0/Screenshot.jpg](http://i5.photobucket.com/albums/y165/nixclusive0/Screenshot.jpg)

however it looks fine in fdisk:

[http://i5.photobucket.com/albums/y165/nixclusive0/2Screenshot.jpg](http://i5.photobucket.com/albums/y165/nixclusive0/2Screenshot.jpg)

---

### Post by jorn on 2006-02-18
It's not my favorite subject, but maybe installing gParted could give you a better overview?
Just a suggestion.
-Jorn-

---

### Post by GTvulse on 2006-02-18
Well.... That's what you get for using PartitionMagic I'm afraid. It ain't what's cracked up to be... :-)

Here is a way to try to fix your partition table. Boot with the live CD, open a terminal window and type ```
sudo -i
```. That will drop you into a supersuer (root) session in that terminal. Type ```
fdisk /dev/hda
``` and at the resulting prompt type ```
x <return> v
```. This will verify the partition table and let you know if it can fix it. You can also type ```
f <return>
``` before writing the partition table to disk with ```
w <return>
``` just to make sure the program assumes there is a change to write to disk. After that try opening the partition table with cfdisk again.

---

### Post by nixclusive on 2006-02-18
[QUOTE=jorn]It's not my favorite subject, but maybe installing gParted could give you a better overview?
Just a suggestion.
-Jorn-[/QUOTE]
Yo thanks for the suggestion! Before using GParted I just tried to look at that  screenshot from 'fdisk -l' and saw that /dev/hdc2 and /dev/hdc6 were starting on the same cylinder (635)! I used fdisk to remove the swap partition and now I have cfdisk working!

With the following output:

[http://i5.photobucket.com/albums/y165/nixclusive0/3Screenshot.jpg](http://i5.photobucket.com/albums/y165/nixclusive0/3Screenshot.jpg)

Now what exactly is that flag on the second partition? And where dod all the space from cyl 636 to cyl 666 go?

I used Gparted to recreate the partition on 636-666 boundary but it simply puts the same thing back! /dev/hdc2 starting on 635 as well as /dev/hdc7 -- dumb thing to use.

---

### Post by nixclusive on 2006-02-18
Ok managed to move the boundry (?) from cyl 635 to cyl 636 for the swap partition! (Yay) So my current situation is this:

```
Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         634     5092573+  83  Linux
/dev/hdc2             635        4865    33985507+   f  W95 Ext'd (LBA)
/dev/hdc5             636         666      249007+  82  Linux swap / Solaris
/dev/hdc6             667        2960    18426523+   7  HPFS/NTFS
/dev/hdc7            2961        4865    15301881    7  HPFS/NTFS
```

Thanks for the 'f' option **dradul**

attached is the 'fdisk -l' output as well as the first 512 bytes from each partitions as well as the drive.

Use:
```
file <filename>
```
to view the files. (except 'snap' - txt file)

cfdisk still gives the error:

```
 FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap 
```

What might be wrong? I suspect the ending cylinders of hdc2 and hdc7 being the same (4865)...now how do I fix that?

---

### Post by GTvulse on 2006-02-18
[quote=nixclusive]What might be wrong? I suspect the ending cylinders of hdc2 and hdc7 being the same (4865)...now how do I fix that?[/quote]

Well.. The problem is not what you think. It is perfectly normal that hdc2 and hdc7 have the same last boundary because hdc7 is the last logical partition inside the primary partition hdc2, that is, the partitions hdc5 to hdc7 are defined in a partition table in hdc2's superblock, not in the MBR. The MBR can only hold 4 primary partitions, a logical "superpartiton", as I like to call them, can hold a lot more, for a total limit of 16 partitions in a DOS style partition including the MBR and logical "superpartitions".

The problem was caused by Partition Magick if that's what you used to partition the disk in the first place. It didn't obey the rules for partitioning DOS style partitions that all partitions must be done in multiples of 8. The solution is drastic. Move the data in hdc6 and hdc7 somewhere safe and delete with fdisk. Save the partition table and then use cfdisk to recreate them. If you tag them as 0x07 for NTFS or 0x0b for Win95 FAT32, you'll be able to format them as FAT32 directly under linux later on or from MS Windows because the disk manager will be able to see them as empty partitions.

---

### Post by nixclusive on 2006-02-20
The following is the diagnostics I did myself, I found some queer results for a partition table:

```
# fdisk -l

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         634     5092573+  83  Linux
/dev/hdc2             635        4865    33985507+   f  W95 Ext'd (LBA)
/dev/hdc5             636         666      249007+  82  Linux swap / Solaris
/dev/hdc6             667        2960    18426523+   7  HPFS/NTFS
/dev/hdc7            2961        4865    15301881    7  HPFS/NTFS
```
Ok this look quite normal. Now check this out:

```
# fdisk /dev/hdc

The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): x

Expert command (m for help): p

Disk /dev/hdc: 255 heads, 63 sectors, 4865 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 254  63  633         63   10185147 83
 2 00   0   1  634 254  63 1023   10185210   67971015 0f
 3 00   0   0    0   0   0    0          0          0 00
 4 00   0   0    0   0   0    0          0          0 00
 5 00   0   1  635 254  63  665      16065     498015 82
 6 00   1   1  666 254  63 1023     498141   36853047 07
 7 00   1   1 1023 254  63 1023         63   30603762 07

Expert command (m for help): q
```
WTF? The ending cylinder for the extended partition (2) is shown as 1023 instead of 4864 (counting from 0 here)!! And what more - the last two NTFS partition (6, 7) are something out from this planet. Partition 6 is ending on cylinder 1023 instead of 2959 and the last partition (7) is starting as well as ending on cylinder 1023 instead of cylinder 2960 and 4864 respectively (see fdisk -l above)!!!

And now for sfdisk - the one recommended for hackers only:

```
# sfdisk -l /dev/hdc

Disk /dev/hdc: 77545 cylinders, 16 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: The partition table looks like it was made
  for C/H/S=*/255/63 (instead of 77545/16/63).
For this listing I'll assume that geometry.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hdc1   *      0+    633     634-   5092573+  83  Linux
/dev/hdc2        634    4864    4231   33985507+   f  W95 Ext'd (LBA)
/dev/hdc3          0       -       0          0    0  Empty
/dev/hdc4          0       -       0          0    0  Empty
/dev/hdc5        635     665      31     249007+  82  Linux swap / Solaris
/dev/hdc6        666+   2959    2294-  18426523+   7  HPFS/NTFS
/dev/hdc7       2960+   4864    1905-  15301881    7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)

```
This is getting weird now. Went right above my head here...
Any partition jedi around to fix this one? Is there a way to fix this without actually screwing existing data?

Or do I really have to rent some disk space for backup? I'm starting to hate MS more and more now.

---

