---
title: "[SOLVED] Ghost 4 Linux &amp;amp; partitioning"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-27
I want to add a new "bare metal" drive. My current drive is Gutsy fully updated, etc. It is a 20 gig drive. My unused drive is 300 gig. 

If I use G4L, after the cloning, how to I handle partitions?

Also, will cloning create a bootable 300 gig drive? I think this is the expected outcome, but have no concrete example to work from.

Does G4L recreate the boot partition, swap partiton, and data partition as they are? How does that effect the new drives ability to work properly?

---

### Post by phr0ze on 2007-11-27
You will likely have to increase the size of your partition after the clone. this can be done with a bootable copy of GParted available on the gparted web site. They also have a copy with a cloning utility included.

---

