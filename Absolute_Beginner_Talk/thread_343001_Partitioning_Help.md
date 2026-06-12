---
title: "Partitioning Help"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-01-20
Hi there,

I'm currently running Edgy from the live disc on my computer and I need to partition a drive in order to install ubuntu. Please see the screenshot below :

[[IMG]http://img444.imageshack.us/img444/458/partitions5ev.th.png[/IMG]](http://img444.imageshack.us/my.php?image=partitions5ev.png)

The reason why I'm posting this is because 2 heads are better than one. I'm just looking for some advice.

* See the two grey, unallocated parts. I need to merge them somehow. The other two NTFS partitions needs to stay as they are, and the same with the extended partition.

How will I merge those two grey ones?

---

### Post by az on 2007-01-20
You need to do some juggling.

Shrink hda3 down to 27 gigs, and then move (copy) the partition to the unalocated space.  Delete the former partition (hda2) and then recreate it right after hda2 by copying it back.  Extend it once again to 36 gigs.  Delete the residual partition if you haven't already and then use the free space which is now in one block.

Back up all your important stuff first.  The partitioner is very careful and safe, but this is a lot of playing around to do.

Nobody has devoted a lot of time to make a partitioner do this easily, which is why you need to do it all by hand....

---

### Post by Contrid on 2007-01-21
> **azz said:**
> You need to do some juggling.

Shrink hda3 down to 27 gigs, and then move (copy) the partition to the unalocated space.  Delete the former partition (hda2) and then recreate it right after hda2 by copying it back.  Extend it once again to 36 gigs.  Delete the residual partition if you haven't already and then use the free space which is now in one block.

Back up all your important stuff first.  The partitioner is very careful and safe, but this is a lot of playing around to do.

Nobody has devoted a lot of time to make a partitioner do this easily, which is why you need to do it all by hand....

Hi there,

Thanks for your comments.
I did what you said and some of my own judgement.
Everything is a-one now.
Thanks again. ;)

---

