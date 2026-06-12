---
title: "partition help"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by sparticus06 on 2008-03-02
I need to reinstall Ubuntu, I royally messed it after trying to do some stuff...anyhoot

i have some pictures and music I don't want to lose and my backup harddrive is busted.
Is it possible to make a separate partition to put my music and pictures on while I reformat everything(except the music). 

I mrunning a duel boot with windows, i plan on getting rid of the windows since I don't use it anymore

 thanks!

---

### Post by sparticus06 on 2008-03-02
here is the fdisk


> Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x412d412d

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 5099 40957686 7 HPFS/NTFS
/dev/hdc2 5100 5161 498015 82 Linux swap / Solaris
/dev/hdc3 5162 5167 48195 83 Linux
/dev/hdc4 5168 9964 38531902+ 83 Linux

---

### Post by ruy_lopez on 2008-03-02
Depending on the size of the music, you should be able to resize, and create enough free space for the music.

The steps are:

Boot up from LiveCD. Use gparted to shrink the partition. Create a new partition in the new free space. Mount the shrunk partition and the new one. Copy files from shrunk partition into new partition. Check they are okay. Then delete the partitions you don't want any more, keeping the small one which you copied your music into.

Then reinstall, but at the partitioning stage of the installer, select "create partition from empty space".

However, you really should create a backup beforehand. So if you lose all the data during the partitioning process, don't blame me.

---

### Post by sparticus06 on 2008-03-02
> **ruy_lopez said:**
> Depending on the size of the music, you should be able to resize, and create enough free space for the music.

The steps are:

Boot up from LiveCD. Use gparted to shrink the partition. Create a new partition in the new free space. Mount the shrunk partition and the new one. Copy files from shrunk partition into new partition. Check they are okay. Then delete the partitions you don't want any more, keeping the small one which you copied your music into.

Then reinstall, but at the partitioning stage of the installer, select "create partition from empty space".

However, you really should create a backup beforehand. So if you lose all the data during the partitioning process, don't blame me.

Thanks! I think I'll backup my photos onto cds before hand, I can always get my music back from my collection.

---

