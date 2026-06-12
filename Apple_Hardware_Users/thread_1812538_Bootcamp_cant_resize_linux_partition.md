---
title: "Bootcamp cant resize linux partition?"
date: 2011-07-26
forum: Apple Hardware Users
---

### Post by madtowneast on 2011-07-26
Hi all, 

I was going to resize my linux partition after solving my other problem, but bootcamp prompts me with:

```
The startup disk cannot be partitioned or restored to a single partition.
The startup disk must be formatted as a single Mac OS Extended (Journaled) volume or already partitioned by Boot Camp Assistant for installing Windows.
```

Does this mean I first ahve to reformat the disk to fat32/nfts and can then resize or is something fishy going on here? Or can I just increase my mac partition using disk utility (erasing the linux partition) without having to reinstall OS X?

Thanks a bunch in advance.

Cheers.

---

### Post by Tylerjd on 2011-07-26
As mac OS cannot read extFS, it wouldn't be able to resize it. Try loading up the Ubuntu Desktop Install CD and load up the GNOME Partitioning Utility (GParted). That will be able to do any partitioning needed, except for expanding HFS (Mac OS) Volumes. To be able to do live partitioning in Mac OS, you need to first wipe any linux partitions (Yes, that means getting rid of those installs), then "Repair" the disk in Disk Utility (can be found under Utilities folder in Mac OS or Mac OS install DVD). That **May or may not** re-allow for live partitioning. For me, it did once, and didn't two other times. For those times, I had to use an advanced hard disk utility like Tech Tool Pro 5 or Disk Warrior (there was one other but the name escapes me now)

---

### Post by madtowneast on 2011-07-27
I figured it out in a very round about way. I just reformatted the drives using gdisk to FAT and then used bootcamp to resize the partitions

---

