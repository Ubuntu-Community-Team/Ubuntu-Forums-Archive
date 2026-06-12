---
title: "[SOLVED] Swap in Manual Partition How? =)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by dmitrijledkov on 2007-07-24
Experimenting installing Ubuntu into virtual machine and I'm doing manual partitioning.

Cause it is virtual drive there isn't any windows partition on my real machine there will be.

I made a large /home partition and 6GB / partition.

But it yells at me that there isn't swap partition. I went back and I don't get what is mount point of swap =))))

Would you please help me to create swap partition =))))) :)

---

### Post by Shazaam on 2007-07-24
Resize your VIRTUAL home partition and make a VIRTUAL swap in the unpartitioned space.

---

### Post by dmitrijledkov on 2007-07-24
I select free unpartitioned space and tells me select size and mount point and file system =(

---

### Post by dmitrijledkov on 2007-07-24
Gotcha swap is as if filesystem type - swap and not ext3 =)))) Solved

---

### Post by Shazaam on 2007-07-24
This is what I did yesterday---
[http://ubuntuforums.org/showthread.php?t=508061](http://ubuntuforums.org/showthread.php?t=508061)
:)

---

