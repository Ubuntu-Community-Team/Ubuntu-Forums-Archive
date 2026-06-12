---
title: "Virtual memory?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by superjdf on 2007-09-08
How do I increase my paging file / virtual memory?

---

### Post by tyggna1 on 2007-09-08
You have to resize your page partition.  It's called Swap in linux--and it's just part of your hard drive.  The bigger this partition, the more "virtual memory."  Typically, your RAM x1.5 is a good size for it.

To resize it, click on System-> administration-> GNOME partition editor, and that will give you a graphical layout of all the partitions on your hard drive.

---

### Post by superjdf on 2007-09-08
ext3          107.63GiB
extended 4.16 GiB
linux swap 4.16 GiB

Those are my partitions, it seems I would have enough to run an application that is requesting
I have 800mb in my paging file?

Hum.

I am trying to run company of heros using the latest wine version but I have hit this wall.

---

### Post by mysticmatrix on 2007-09-08
> **superjdf said:**
> ext3          107.63GiB
extended 4.16 GiB
linux swap 4.16 GiB

Those are my partitions, it seems I would have enough to run an application that is requesting
I have 800mb in my paging file?

Hum.

I am trying to run company of heros using the latest wine version but I have hit this wall.

Under Linux, your Linux Swap partition is your *page file*, to borrow the term windows uses.
Thus you have 4.16GB of virtual memory available to Linux Programs.

Your problem is more specific to Wine, and perhaps you should check out gaming forums at ubuntuforums.org for specific details regarding Company of Hero

---

