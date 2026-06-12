---
title: "Partitions"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by dunklegend on 2006-09-08
I have 4 partitions:

1 NFTS for Windows XP
2 ext3 1 for linux and 1 for /home
1 for swap

I have extra unallocated space (about 100 GB) but I can't make a new partition because I already have the 4 primary partitions.

What can I do to make this partition without having to reinstall linux?

---

### Post by Tarvok on 2006-09-08
Hmm... can swap be a logical partition?

If so, delete swap, recreate as logical, and there ya go. (I hope you get what I'm saying. I can't seem to remember the technical language for partitions right now!)

---

### Post by Brownedwg89 on 2006-09-09
yes swap can be a logical
so just delete swap make a large(probably the whole 100GB)extended partition, and remake the new swap a logical and add whatever new logical partitions you want

---

