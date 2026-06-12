---
title: "Resizing ext3 partition"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by Signguyhuss on 2006-04-24
Hello All..Currently I have 
20 gig -Primary [Windows install NTFS] 

5 gig - Primary [ubuntu install -ext3 /]
5 gig - Logical [fat 32]
300 meg - SWAP
100 gig - logical[ntfs]
100 gig -logical[ntfs]


I was wondering. If i resized the 5 gig primary Ext3 root partition using Partition Magic 8.0 in Windows, would this screw anything up? Or would ubuntu still run fine?
I can let it take space from any of the drives, and i was thinking of moving  5 gigs to the ext3 from one of the logical drives or possibly from the main win install partition.

Thanks in advance

---

### Post by nalmeth on 2006-04-25
Resizing EXT3 is less risky then risizing ntfs, but you should still backup you data, if you have anything important.
There are no guarantees

---

### Post by aysiu on 2006-04-25
I don't see why you need Partition Magic.
Just use a live CD and GParted or QTParted.
By the way, you can't add to the beginning of a partition, only to the end of it.

---

### Post by adamkane on 2006-04-25
My understanding is that you have to "turn off" journaling, which essentially turns your ext3 filesystem into an ext2 filesystem. You then must try to resize the unjournaled partition with gparted, and then rejournal the partition back to ext3.

This doesn't always work however, and you will likely need to move your data off the partition, delete the partition, recreate the new partitions, then move the data back onto your new partition.

---

### Post by aysiu on 2006-04-25
[QUOTE=adamkane]My understanding is that you have to "turn off" journaling, which essentially turns your ext3 filesystem into an ext2 filesystem. You then must try to resize the unjournaled partition with gparted, and then rejournal the partition back to ext3.[/QUOTE] I've resized Ext3 partitions and have never had to turn off journaling (I don't even know how to turn it off). The partition to be resized must be unmounted, though, which is probably why you need a live CD.

---

### Post by nalmeth on 2006-04-25
> I've resized Ext3 partitions and have never had to turn off journaling (I don't even know how to turn it off). The partition to be resized must be unmounted, though, which is probably why you need a live CD.
second that

---

