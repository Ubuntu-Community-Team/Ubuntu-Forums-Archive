---
title: "Will Gparted repartition a Linux and an XP partition"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-04-13
I have Ubuntu and XP installed in a dual boot system.  Ubuntu is the smaller partition and I wish to make it the larger partition.  Will I be able to change both the Linux and the XP partitions using Gparted or does Gparted only resize Linux partitions?

---

### Post by thefoolisme on 2007-04-13
Gparted will work on linux, Windows (FAT32, NTFS), and Mac OS partitions.  Basically, you can use it for any partition.  Make sure before you shrink your Windows partition that you defragment it twice to get it ready.

---

### Post by a.v.l on 2007-04-13
> **thefoolisme said:**
> Gparted will work on linux, Windows (FAT32, NTFS), and Mac OS partitions.  Basically, you can use it for any partition.  Make sure before you shrink your Windows partition that you defragment it twice to get it ready.

Many thanks, would you know of a good "how to" for using Gparted this is new to me?

---

### Post by wataboutbob on 2007-04-13
its pretty simple really. Its only a question of choosing the partition block (whether it be NTFS / ext3 / Linux-SWAP or whatever) that you want to resize and use either the slider to resize it or give a specific size.

I don't know if you can resize your linux partition while logged in. Personally, I used the LiveCD to boot into temporarily and used the gparted included in it to resize my partition.

---

### Post by a.v.l on 2007-04-13
> **wataboutbob said:**
> its pretty simple really. Its only a question of choosing the partition block (whether it be NTFS / ext3 / Linux-SWAP or whatever) that you want to resize and use either the slider to resize it or give a specific size.

I don't know if you can resize your linux partition while logged in. Personally, I used the LiveCD to boot into temporarily and used the gparted included in it to resize my partition.

Thanks again, I've just downloaded the liveCD and will give it a try this evening.

---

