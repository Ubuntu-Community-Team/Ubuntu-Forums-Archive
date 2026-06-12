---
title: "[SOLVED] Newbie went overboard with GParted... help"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by TreeHugger52 on 2009-01-05
Hello all,

A while ago I installed hardy heron on my Macbook Santa Rosa on a small partition, as I was just giving Ubuntu a try. I've come to prefer Ubuntu over OSX, and decided to increase the disk space available to Ubuntu. I used GParted's gui (I know... I know...) to reduce the size of my OSX partition by 55GB and created a new ext3 partition in this space. In doing so, I noticed 15 GB of unallocated space at the end of the drive, and I created a ext3 partition in this as well. It looked like everything went well- GParted was successful. I installed some normal auto updates and restarted, but Ubuntu was no longer a boot choice- rEFIt gave me the option to boot into OSX (which works just fine, it's what I'm using now, and the HD partition is the correct, smaller size) or something like a "remnant operating system", with the icon of four grey diamonds arrayed in a larger diamond. I tried this, but just got a text screen with an error something like "Operating System Missing".

I used OSX's Disc Utility, which found the following partitions-

Macintosh HD- 150 GB
disk0s3- 14 GB, FAT32 (the original Ubuntu partition, but why FAT32?)
Linux Swap- 1.9 GB
disk0S4- 54.5 GB FAT32 (should be the new partition, why is it FAT32??)
disk0S5- 15 GB (another new partition, but also FAT32??)

Can someone help me get back into Ubuntu? A complete reinstall of Ubuntu isn't preferable, but would be okay. I backed everything up.

A sheepish thank you.

---

### Post by pxwpxw on 2009-01-05
Just run the refit Partitoing Tool and let it resync your MBR will probably fix it, if you have not actaully changed the ubuntu root partition.

---

### Post by bryonak on 2009-01-05
Does [this]("http://ubuntuforums.org/showthread.php?p=6497622#post6497622") help?

Besides, one of your partitions should be where the EFI configuration and data resides. It needs a separate partition because it doesn't fit into the master boot record of your hard drive.
Are you sure you didn't delete it?

---

### Post by TreeHugger52 on 2009-01-05
Thanks for the speedy replies- Ubuntu community support is wonderful.

The rEFIt partitioning tool was the first thing I tried. It synced the MBR, but didn't allow me to boot into Ubuntu. The EFI partition is the first thing on the drive- I didn't delete it. I didn't make any changes to the Ubuntu root partition in GParted- I intentionally left it alone.

It looks like the rEFIt partitioning tool is reading the OSX partition as being too large, it takes up the vast majority of the disc according to rEFIt, such that it engulfs the Ubuntu root partition. The tool currently says that everything is synced and no changes are required. Should I try to reinstall rEFIt and hope that it reads the drive correctly? This seems drastic.

Thank you very much for your help.

---

### Post by TreeHugger52 on 2009-01-05
The rEFIr partitioning tool produces this output:

GPT Partitioning table
#   Start LBA     End LBA     TYPE
1      40         409639      EFI System (FAT)
2    409640       309460094   Mac OSX HFS+
3   423772200     453069075   Basic Data
4   453069076     456975326   Linux Swap
5   309460095     423772199   Basic Data
6   456975327     488392064   Basic Data


MBR Partitioning Table
#   Start LBA     End LBA     TYPE
1       1         409639      EE  EFI Protective
2    409640       309460094   AF  Mac OSX HFS+
3*   423772200    453069075   83  Linux
4    453069076    456975326   82  Linux Swap/Solaris

---

### Post by cyberdork33 on 2009-01-05
The problem is that your Ubuntu partition is now partition #5 which is not bootable (because it is not in the MBR partititon table).

If you want to repair things, you can delete your swap partition, resize the first linux partition to take up the space, then use the last linux partition as swap instead.

---

### Post by TreeHugger52 on 2009-01-05
Just curious, how do you know the ubuntu root is in partition 5? Was it my description, or did you somehow get that from the rEFIt output?

---

### Post by cyberdork33 on 2009-01-05
> **TreeHugger52 said:**
> I used GParted's gui (I know... I know...) to reduce the size of my OSX partition by 55GB and created a new ext3 partition in this space.
It is a very high probability that EFI is #1 and OSX is #2, so the "new" partition you inserted would be #3

The partition following this in your output was a swap (#4), which means that your root has to be > #4.

Additionally,

> **TreeHugger52 said:**
> In doing so, I noticed 15 GB of unallocated space at the end of the drive, and I created a ext3 partition in this as well.

Says that the very last partition is not your root partition either, so your root must be #5 since that is the only one left. If you want to check, boot from the Ubuntu LiveCD and mount sda5. It should have your Ubuntu files.

---

### Post by bryonak on 2009-01-05
> **TreeHugger52 said:**
> Just curious, how do you know the ubuntu root is in partition 5? Was it my description, or did you somehow get that from the rEFIt output?

It's called magic!

You wrote in your initial posting: reducing the size of your OSX partition by 15 GB and making a new ext3 partition there tells us that Ubuntu, which you had already installed before, is not on this partition. There's just #5 or #6 left, the latter being that "15 GB of unallocated space at the end" you noticed, which leaves #5 (which is the biggest partition after the OSX one).

Err, or was the word logic? ;)


Early BIOSes could only count up to four, so there is that cap for four primary partitions. This limitation is long overcome, but for the sake of tradition / being too lazy to change, many boot systems only look at the first four partitions.

To complement cyberdork's posting:
If your OSX partition has the desired size, you can do all the other resizing/moving from the Ubuntu liveCD. When using gparted (which you should be familiar with by now), make sure that you "deactivate" the swap partition (there's a right click option for that) before moving it.
Also trying to do as few moves/resizes as possible will reduce the overall time it takes.
And always think twice before hitting that Apply button.

---

### Post by TreeHugger52 on 2009-01-05
I implemented all of these suggestions and was sure that the root partition appeared in the MBR table, I updated to the current version of rEFIt, but was unable to get Ubuntu to boot. Reinstalling Ubuntu fixed the problem, and I'm writing this running 8.04, so the problem is solved.

It looks like I damaged the root partition when I used GParted for the first time. I didn't use the live cd- I ran GParted while in Ubuntu. I realize that this is risky if you edit mounted partitions, but I thought I was safe by not touching the root partition.

Thank you much for your help and comments.

---

### Post by cyberdork33 on 2009-01-06
Please mark this thread as solved from the Thread Tools Menu at the top of the page.

---

