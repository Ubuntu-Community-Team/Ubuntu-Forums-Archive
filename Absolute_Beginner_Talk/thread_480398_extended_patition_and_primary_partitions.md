---
title: "extended patition and primary partitions"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-21
i'm attemtping to partition manually for the sake of multiple os booting.... but i have a question...does the extended partition have to be of equal size to the primary partition? The primary is root right? Then what is extended?

---

### Post by Inxsible on 2007-06-21
Check this link out for more info on primary and extended partitions
 
[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

---

### Post by starcraft.man on 2007-06-21
> **maddot said:**
> i'm attemtping to partition manually for the sake of multiple os booting.... but i have a question...does the extended partition have to be of equal size to the primary partition? The primary is root right? Then what is extended?

This takes a bit more than just a simple explanation. Primary partitions are the top level partitions. Extended were created after to fill the need of more than 4 partitions (the limit with Primaries), they can of course be filled with up to 4 logical partitions. Extended partitions create a simple shell that has the maximum size of whatever you allocated it, and that space gets distributed however you like amongst any number of logicals inside it.

Now as to specific things you probably want to know. Any Windows Prior to (and including) XP has to be installed to C as a primary (Vista is exception I believe...). Linux can be easily installed into any extended/logical partition without any problems from what I've heard, this applies equally to the root and any other mounted partition.

As to your question the extended partition equal to the primary, no, you can make any of the partitions any size you want they are independent of each other. The only exception is that extended partitions are limited to what you allocate at the beginning, you can't expand beyond that without first increasing the size of the extended partition, and then the logical inside specifically.

For more info on partitioning and using gparted (I assume your using that), check [here]("http://gparted.sourceforge.net/documentation.php").

Hope I got all that right :).

---

### Post by indytim on 2007-06-21
> they can of course be filled with up to 4 logical partitions. 

I believe you can go beyond 4 partitions within an extended partitions.

IndyTim

---

### Post by LaRoza on 2007-06-21
You can only have up to four primary partitions, in an extended partition, you need to set up a logical drive, otherwise you cannot use the partition.

---

