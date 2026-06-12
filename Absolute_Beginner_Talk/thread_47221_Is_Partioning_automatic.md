---
title: "Is Partioning automatic?"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by maryjo on 2005-07-07
I have a little "housecleaning" to do with my system and then I can attempt to install to my hard drive but I want to be sure of something.  If all I have on my hard drive is C & D drives (both XP Pro), do I need to partition before installing Ubunto or will it do it automatically?  If it does it automatically, do I get the option as to what size the partition should be?

I only have XP Pro now.  I will be keeping XP Pro & adding Ubunto.

Mary Jo

---

### Post by Kvark on 2005-07-07
You can either free up space for a new partition on beforehand with your favourite partitioning tool or use the install program to resize or remove partitions to free up space.

In any case, make a backup before messing with your hard drive.

[COLOR=Red]edit:[/COLOR] it looks like they might come up with some good advice in [this thread](http://ubuntuforums.org/showthread.php?t=46741)

---

### Post by gil-galad on 2005-07-07
[QUOTE=maryjo]I have a little "housecleaning" to do with my system and then I can attempt to install to my hard drive but I want to be sure of something.  If all I have on my hard drive is C & D drives (both XP Pro), do I need to partition before installing Ubunto or will it do it automatically?  If it does it automatically, do I get the option as to what size the partition should be?

I only have XP Pro now.  I will be keeping XP Pro & adding Ubunto.

Mary Jo[/QUOTE]
 The ubuntu installer has a partitioning utility.  If you are comfortable with editing partitions you should be able to figure it out. 

Just be sure you don't overwrite the windows partition. :)

---

### Post by maryjo on 2005-07-07
Thank you for such a speedy response.  

I hoped to get up and running tonight but I can already tell "the flesh is weak" but I am going to try clean up my MBR (linspire is stuck in there) tonight.


Mary Jo

---

### Post by aysiu on 2005-07-07
Most likely your C: and D: drives are formatted with NTFS or FAT32. Even if your D: drive is FAT32, Linux cannot be installed on it. Linux can read from and write to FAT32, but it cannot be installed on FAT32. Ubuntu uses EXT3.

So, you should either resize your D: drive and make an EXT3 partition or just reformat your D: drive as EXT3 (this can be done during the Ubuntu install).

---

### Post by manicka on 2005-07-07
you can restore your mbr with the windows xp install disk to bring it back to a windows only then overwrite it during the ubuntu install

---

### Post by az on 2005-07-07
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by polo_step on 2005-07-07
I dunno if anyone mentioned it or not, but I've read in various dual-boot how-tos and been repeatedly told that one should defrag the drive before setting up new partitions from unused disk space, in order to get all the existing data in one place on the drive.

True?  I don't claim to now, but it makes sense.

---

### Post by manicka on 2005-07-08
[QUOTE=polo_step]I dunno if anyone mentioned it or not, but I've read in various dual-boot how-tos and been repeatedly told that one should defrag the drive before setting up new partitions from unused disk space, in order to get all the existing data in one place on the drive.

True?  I don't claim to now, but it makes sense.[/QUOTE]
 this is usually only necessary when resizing an existing partition. Free space is Free space and has no data on it. Having said that though, a defrag never hurts at any time

---

