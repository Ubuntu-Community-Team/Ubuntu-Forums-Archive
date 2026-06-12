---
title: "Installation Problem"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-31
After much ado, i finally burnt a working image of ubuntu and started the installation! and wow..my first experience with ubuntu live -- - - - simply amazingly awesome!! well anyway the installation got through and everything, now the problem came when i tried to partition disks. I made a partition from my currect C: to 20 GB Ext 3, and name was "/" then i tried to make a swap partition of 2 gb, which i was somehow not able to. Can someone guide me? 
thanks in advance
sibot

---

### Post by sibot on 2007-05-31
and what should be the format of the swap partition? ext3?

---

### Post by rillip on 2007-05-31
There's a filesystem dedicated to swap that would be better. Just browse through, it says something like linux-swap.

When you say it couldn't, can you elaborate on what happened?  Remember that you can only have four physical partitions on the same drive - you haven't given your partitioning scheme so I don't know if this is an issue.  If you have four and need to create more,  you'll have to create logical partitions rather than extended.  It makes the partitions inside the one partition.

---

