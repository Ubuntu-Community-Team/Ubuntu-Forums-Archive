---
title: "fdisk problem - unable to write the partition table, sector size is 2048 (not 512)"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by wokka on 2006-04-10
I am trying to delete and create new partitions.

After running fdisk /dev/hda i receive the following messages;

[I]ubuntu@ubuntu:~$ fdisk /dev/hda
You will not be able to write the partition table.
Note: sector size is 2048 (not 512)
Device contains neither a valid dos partition table, nor Sun, SGI, or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only, until you decide to write them. After that, of course, the previous content won't be recoverable.

Warining : invalid flag 0x0000 of partition table 4 will be corrected by w(rite).[/I]

How do we go about trying to change the sector size from 2048 to 512, which will hopefully allow me to write to the partition table?

I have tried using gparted from the ubuntu live cd, although have been unsuccessful.

Any help would be appreciated.

---

### Post by Sef on 2006-04-21
Download system rescue cd.

[http://freshmeat.net/projects/systemrescuecd/]("http://freshmeat.net/projects/systemrescuecd/")

---

### Post by jorn on 2006-04-21
"Warining : invalid flag 0x0000 of partition table 4 will be corrected by w(rite)."
Does't that correct the sectorsize when pressing the write botton?

---

