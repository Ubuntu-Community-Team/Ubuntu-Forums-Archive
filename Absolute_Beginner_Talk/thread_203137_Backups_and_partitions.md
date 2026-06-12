---
title: "Backups and partitions"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by bohboh on 2006-06-24
I want to backup my entire system and have a couple of questions:

1. If i backup everything from root will it backup files in use, or is there an issue with files in use. Do i need to be logged out?

2. If i backup my entire system, do i need to worry about the partitions sizes, lets say my entire hard drive goes and i need to replace it. How would i know how i paritioned it? Would i need to partition the new drive exactly the same as my old one? Can i get a report/breakdown of my paritions for reference?

Many thanks

---

### Post by The Mekon on 2006-06-24
I am not sure that this is any use but I have two identical (in size) hard drives on my computer and I use HDCLONE on a floppy disk to literally clone the working drive to the backup drive.

I have had problems with switching from 5.10 to 6.06 and was able to swap the drive cables and bootup using my cloned drive.

Note HDClone is freeware and can only back up a complete drive to another of identical or larger capacity.

---

### Post by bohboh on 2006-06-25
I dont have the luxury of a second hard drive so i plan to zip and tar the entire lot, i just dont know about the partitions.

---

### Post by verbatim210 on 2006-06-25
i'm still new to ubuntu but from a windows point of view...

zip is NOT a backup method.  i've tried norton ghost, won't work.  i've read the new norton ghost is compatible with ext3. vesion 9 or 10 or something.

for those without the luxury of version 9 or 10 or something, theres a program called G4L, ghost for linux.  

its open source so, i've yet to try it...

---

### Post by jhr79 on 2006-06-25
I'm using Partimage, [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page), from SystemRescueCd, [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page), to backup my root file system. For home I'm using just tar and gzip. So far those has worked well and I have even restored my system from image to test it.

---

### Post by bohboh on 2006-06-25
What do you restore to? Do you have to reformat your hard drive in any way?

---

### Post by jhr79 on 2006-06-25
[QUOTE=bohboh]What do you restore to? Do you have to reformat your hard drive in any way?[/QUOTE]

If this was meant for me, Partimage is working like Ghost so it's not actually formatting the drive but restoring it to the state where it was when the image was created. I think this is the easiest way to backup the system (but I wouldn't use it for documents etc.)

---

### Post by bohboh on 2006-06-25
To clarify, are you saying that i can literally take a brand new unformatted hard drive and restore to that without having to do anything else to the disk?

---

### Post by jhr79 on 2006-06-25
[QUOTE=bohboh]To clarify, are you saying that i can literally take a brand new unformatted hard drive and restore to that without having to do anything else to the disk?[/QUOTE]

In that case you need to create a partition for restoring as notes in the documentation, [http://www.partimage.org/Partimage-manual_Usage#How_to_restore_a_partition_from_an_image_file](http://www.partimage.org/Partimage-manual_Usage#How_to_restore_a_partition_from_an_image_file). There is also instructions on how to save partition information for those cases. Never needed to try that anyhow.

---

