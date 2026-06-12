---
title: "GParted says I have 10.32GiB taken up, but it's only 2.5"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-31
What is this?

I can't shrink a partition, because I only have 2.5GiB of stuff on, but GParted says I have 10.32GiB taken up.

Any ideas???

---

### Post by gohanssjn on 2007-05-31
Ok, even weirder, under System Monitor, I get 

/dev/sda2 total:11.9GiB 
Available: 8.8GiB
Used: 2.6GiB

Help?

---

### Post by gohanssjn on 2007-05-31
Sorry, should have added:

THhs partition is from a restore through partimage if that matters.

---

### Post by freebird54 on 2007-05-31
Well - hidden files can create this kind of confusion.  What kind of partition (and for what OS) is this that gives you the problem?

---

### Post by gohanssjn on 2007-05-31
> **freebird54 said:**
> Well - hidden files can create this kind of confusion.  What kind of partition (and for what OS) is this that gives you the problem?

Ubuntu ext3.

I finally got it to resize from 20Gib to 10GiB, and now it's sizing from 10GiB to 2.75GiB, so hopefully this will work!

---

