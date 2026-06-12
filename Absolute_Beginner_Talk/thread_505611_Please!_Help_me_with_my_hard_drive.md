---
title: "Please! Help me with my hard drive"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by rainontin on 2007-07-20
Hi, i know there's a lot of themes about hard drives, but i'm crying and dying right now, So here's my problem, I have a 250gb Sata drive, With 2 NTFS partitions, 1 for windows and programs and the other one for Documents (this is the most important), And of course i have a Linux Swap and a EXT3  and  i was dual-booting win xp and ubuntu, 

Somehow my xp got pretty wasted, So i decided to format the partition of windows and reinstall that, I did that with partition magic in windows, It was pretty quick and everything, i booted and i saw winxp in grub, So i pushed enter and it say to me, "can't be found" etc. So i pressed reset and entered in ubuntu, ubuntu didn't recognized my two ntfs partitions, because i haven't closed windows right, But gparted was seeing the two partitions, i tried to run ntfsfix, and ntfsfix told me that it wasn't possible to do a fix on the partitions,

I got desperate, because my documents partition was not readable, Then i tried to install windows again, Got 100% and booted, i was expecting to boot windows without grub, but it didn't :( . Then i put the supergrub cd and booted from there, It didn't boot anything from the ext3 and i suppose and the first ntfs, because an error of the cylinder size.

So here i am running ubuntu ff from the live cd, seeing that gparted sees my hd with anything in it, But nautilus recognizes and mounts the ntfs partition with windows (installed) and the size that i assigned for it but not anything else, 
I'm pretty nooooooob, and so f!"·$d up, Please Help, i don't mind about the ext3, windows or anything, i miss my documents partition. HELP!

---

### Post by grishenko2000 on 2007-07-20
whats the output from 
```
sudo fdisk /dev/hda
p
q

```

---

### Post by rainontin on 2007-07-20
> **grishenko2000 said:**
> whats the output from 
```
sudo fdisk /dev/hda
p
q

```

Can't open dev/hda and what about the p and the q?

---

### Post by grishenko2000 on 2007-07-20
i was assuming that /dev/hda was the name of your harddrive if you have gparted open that should say what device it is and replace /dev/hda with that (might be /dev/sda or something else)

the "p" prints the partitions for that drive and "q" quits fdisk.

---

### Post by asmoore82 on 2007-07-20
yea... preeetty much all non-UNIX partition software is trash IMO.

---

### Post by rainontin on 2007-07-20
ok after sudo fdisk /dev/hda this is what appeared:
The number of cylinders for this disk is set to 30515.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

After P:
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      105929      225457   960110992   50  OnTrack DM
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      117098      150914   271628592+  74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?          42          42           0   69  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4          166584      166587       24662+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

And Thanks in advance of any input or help.

---

### Post by grishenko2000 on 2007-07-20
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by rainontin on 2007-07-20
Great i will try this. Wish me the best luck!

---

### Post by rainontin on 2007-07-20
I recovered my hard disk table, look:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15861   127403451    7  HPFS/NTFS
/dev/sda2   *       15862       18171    18555075   83  Linux
/dev/sda3           18172       30515    99153180    f  W95 Ext'd (LBA)
/dev/sda5           18172       18428     2064321   82  Linux swap / Solaris
/dev/sda6           18429       30515    97088796    7  HPFS/NTFS

```

How about that, now all i have to do is set EXT3 to boot and that's all, F#$ windows, i'm going to stay with ubuntu only. It's the second time that i got this problem.:guitar:

---

### Post by rainontin on 2007-07-20
Any help on how in the world  can i get rid of grub arrange the masterboot and boot from ubuntu only?

---

