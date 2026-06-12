---
title: "merging two ext3 partitions ??"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ambush_xx on 2007-06-05
I was tring to increase the size of my home partition so i created a partion from one of my ntfs drive , i was hopin that i could merge the 2 partitions from a live cd using gparted 

But there is no option for that on Gparted or Qt parted

is there any way to do this..

---

### Post by starcraft.man on 2007-06-05
> **ambush_xx said:**
> I was tring to increase the size of my home partition so i created a partion from one of my ntfs drive , i was hopin that i could merge the 2 partitions from a live cd using gparted 

But there is no option for that on Gparted or Qt parted

is there any way to do this..

Easiest way I can think of is the following, for the example I'll call them partitions A and B. So start in gparted live CD or the gparted from the live CD and resize A (arbitrary, pick the one that has the most data on it) so that it has enough free space on it and can completely hold all the data on B. Then from the live CD mount A and B and copy over all the files you want from B -> A. Now A contains all the data and B is just a copy. Unmount both drives A and B and then delete drive B. Then, you are free to resize A with all the free space now made. End.

I believe thats the best means, hope I made it clear :).

Oh and be careful, resizing can cause data trouble (back up anything vital to your life)... but in my experience it should be fine.

---

### Post by ambush_xx on 2007-06-05
I dont know if you got my problem correctly
my problem is that i freed up space from Hda 7 there and made some unallocated space hoping that i will be able to expand my /home patition(Hda 9 here)

but there is no option to expand the /home parttion over the free space with gparted or qtparted 
I tried the to make an ext 3 partition with the free space and merge the partitions as required but again thre is no option to merge to partiton in gparted


I there any hope...



   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1187     9534546    c  W95 FAT32 (LBA)
/dev/hda2            1188        9733    68645745    f  W95 Ext'd (LBA)
/dev/hda5            1188        4375    25607578+   7  HPFS/NTFS
/dev/hda6            4376        7305    23535193+   7  HPFS/NTFS
/dev/hda7            7306        8808    12072816    7  HPFS/NTFS
/dev/hda8            8809        8859      409626   83  Linux
/dev/hda9            8860        8881      176683+  83  Linux
/dev/hda10           8882        8956      602406   82  Linux swap / Solaris
/dev/hda11           8957        9733     6241221   83  Linux
ambush@ambush-desktop:~$

---

### Post by starcraft.man on 2007-06-05
Hmmm, my bad... guess I miss read.

Holy... that is a lot of partitions. Do you use them all?

Anyway, I believe I know what the problem is. When your using a partitioner (applies to all far as I know, the automatic ones will simply move data and partitions for you) you have to create partitions in a certain order, for example X Y Z. Say those are just 3 simple ext3 partitions with data on them. If I delete Z the free space is at the end of the partitions, now I want to add that free space to X. There is a problem, Y is in the middle and the space has to be adjacent to be added/used (way the system works). So, all you have to do is move the free space so its before Y and next to X. There is a function in gparted called "move" part of resize I think, all you do is select the partition in the middle (Y in my case) and move the free space after it, to before the partition. Then repeat until it is up to and next to the one you want to add to (X in my case, and only requires one move of data).

All has to do with the way partitions are created/managed. Other partitions (paid ones) will do this automatically for you without telling ya.

I hope I got what you mean this time :p.

---

### Post by Gina on 2007-06-05
I think if you have 2 adjacent partitions you can delete the upper one and resize the lower one to use the space freed up.  I've read that you can't do it the other way round.  ie. you can increase from the top but not add space at the bottom of a partition.  I have not tried this as yet so I can't say it'll work.

---

### Post by ambush_xx on 2007-06-05
> **Gina said:**
> I think if you have 2 adjacent partitions you can delete the upper one and resize the lower one to use the space freed up.  I've read that you can't do it the other way round.  ie. you can increase from the top but not add space at the bottom of a partition.  I have not tried this as yet so I can't say it'll work.

Thats exaclty what i am not able to do i.e resize the lower partition to take up free space from the higher partition.
I am trying to increase the size of hda 9 so i made some free space above it but there is no way to increse the size to take up the space in gparted

---

### Post by ambush_xx on 2007-06-06
Never mind ..i just backed up and deleted my home partition and and merged it with some free space above and copied the contents back to the newly formed bigger partition..

---

