---
title: "Primary / Logical / Extended Partitions"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-01-30
When repartitioning, the options are primary, logical, swap, and extended. What exactly does each do and which is the best to use?
My current hard drive is partitioned: Root as Primary, Home as Logical, with Linux-swap, and Extended. Is it the optimum configuration for a 100% Ubuntu installation?

---

### Post by Jussi Kukkonen on 2007-01-30
That partitioning scheme works fine.

HOWTOs are you friend in generic linux issues like this:  [http://www.faqs.org/docs/Linux-mini/Partition.html](http://www.faqs.org/docs/Linux-mini/Partition.html). Basically, the only reason this is complicated is the ***-backwards Intel design that we're stuck with: There can be only four partitions (these are called primary). Fortunately one of those can be subpartitioned (this extended partition houses all of the other logical partitions). Swap is used as a place to throw memory pages that the OS thinks aren't going to be needed in the near future, this is done to have more memory available. Swap is only needed on the disk the OS boots from.


Edit: Hmm, *** is a forbidden word here it seems. I must remember that the next time I have something to say about ***, the domesticated horse-related animal, or ***, the gene.

---

### Post by housam on 2007-01-30
You can read [this guide ]("http://community.linux.com/howtos/Partition/index.shtml")in partitioning

---

### Post by Stunt Double on 2007-01-30
Thanks for the helpful link.
From what it says, it doesn't matter whether /home is a primary or logical partition. Either way, if I need to re-install Ubuntu, my files will be safe in /home.
Am I reading that correctly?

---

### Post by taurus on 2007-01-30
Yes, your /home would be safe providing that you don't format it.  Just mount whichever partition that has /home on to /home.

---

### Post by jvc26 on 2007-01-30
If you install /home to a different partition other than the one you install /, then when you reinstall the /home partition wont be affected - you can choose on the manually edit partitions table not to format it and to mount it at the /home point. That will then install the new system to / without wiping /home.
Il

---

### Post by K.Mandla on 2007-01-30
> **Stunt Double said:**
> Is it the optimum configuration for a 100% Ubuntu installation?
The only other partitioning tweak that might improve things is to separate out a /boot partition, keep it small (like 100Mb) and use a very basic file system on it (like ext2). However, the benefits are up for debate, since most modern machines would hardly notice the improvement by doing that. 

Aside from that, if you want to use a root filesystem that doesn't play well with Grub (like xfs), you might also consider a separate /boot partition.

Was that more information than you wanted? :roll:
> **Jussi Kukkonen said:**
> Edit: Hmm, *** is a forbidden word here it seems. I must remember that the next time I have something to say about ***, the domesticated horse-related animal, or ***, the gene.
(That is correct. ;) )

---

### Post by Stunt Double on 2007-01-30
Thanks for the help.

---

