---
title: "A few quick questions about partitioning for dual boot"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Zigon on 2007-07-05
I plan on dual booting windows and Ubuntu. Right now my laptop has two partitions, the primary 80gig NTSF partition where windows XP is Installed and a few mb's of allocated space. When resizing and creating a new partion the primary 80gig, do I make another primary ext3 partition using the unallocated space where linux will be installed and then a logical partition for the linux-swap? So far I think that's how it works. Also, whats the difference between ext2, ext3, logical and primary?

Thanks :)

---

### Post by Skrynesaver on 2007-07-05
First logical and primary partitions,
You can have up to 4 primary partitions, one of these can be an extended partition within which you can then have logical partitions, logical partitions as a result start numbering at 5.

ext3 is ext2 with journaling (simplified answer, for a more complex answer try google ;) )

You can fit all the partitions you need as primary partitions.  So I;d recomend splitting your space into ext3 and swap with swap being twice RAM

---

### Post by Zigon on 2007-07-05
Thanks, that cleared up a couple things for me. But once I'm done partitioning should I end up with 1 ext3, 1 swap, and 1 NTSF partition for windows?

---

### Post by Skrynesaver on 2007-07-05
That is the ideal first setup, in the longer term you may want to consider a seperate /home partition so that you can play with other ditribution but for a starting system that looks like an ideal setup

---

### Post by Zigon on 2007-07-07
What does it mean when I can't choose logical? It's there I can't have focus on it though, so I can only choose primary or (extension?).

---

### Post by Skrynesaver on 2007-07-07
Sorry, I wasn't clear, extended is a special type of primary partition that can contain logical partitions, you have to have an extended partition to house the logical partitions in

---

