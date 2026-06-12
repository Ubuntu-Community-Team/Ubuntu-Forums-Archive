---
title: "Can I use the same external USB 2.0 HD to back up a Ubuntu and an XP computer?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Steve Angelidis on 2008-03-16
I bought a 500G LaCie external HD for backup and extra storage. Can I use it for both my wife's XP machine and my Ubuntu Gutsy laptop? If so, how would I go about setting it up?

Thanx.

---

### Post by PeterJS on 2008-03-16
A hard drive is just storage, as long as you format it with a filesystem both systems can use, there's no reason why you can't use the same container for multiple backups. As for the how, that depends on the tools you plan to use for backing up the machines.

---

### Post by bsharp on 2008-03-16
As Peter said, it doesn't matter, but if you are doing a backup then you might want to create a separate partition for each one for simplicity's sake.

---

### Post by Steve Angelidis on 2008-03-16
The drive came formatted as FAT 32. Should I reformat to NTFS and partition it on the XP machine? The docs include directions for doing so and say that NTFS would give better performance.

Would Ubuntu recognize a partition created by XP?

---

### Post by PeterJS on 2008-03-16
A partition is a partition is a partition*. You could create a partition with a Mac, format it with windows, and ubuntu could read it just fine. Ubuntu can both read and write NTFS, so if you're going to go the single partition route that's what I would suggest. If you're going to do one partition per back up as bsharp suggested, might as well make the windows one NTFS, and the linux one ext3, so each system gets to use it's native file system.


*unless it's an Open BSD pseudo partition, or LVM, or any number of logical oddities, I guess I should amend that a physical partition is a physical partition.

---

### Post by niteshifter on 2008-03-16
Yes, you can use NTFS. The "better performance" is not speed, it's reliability. As bsharp said, two partitions is a good idea. Ubuntu via ntfs-3g can read / write NTFS partitions but there are restrictions with respect to writing (cannot write compressed files, cannot handle encryption). So I would (and did on my external HD) set a partition up with ext3.

---

### Post by Steve Angelidis on 2008-03-16
Thanks all!

I'll give it a try. Ext3 for Ubuntu and NTFS for XP.

I appreciate your input on such a simple issue.

Feel kind of like a kid in grade 2 asking Stephen Hawking for help with my math homework....

---

### Post by bsharp on 2008-03-16
> **Steve Angelidis said:**
> Feel kind of like a kid in grade 2 asking Stephen Hawking for help with my math homework....
That's going into my sig....

---

