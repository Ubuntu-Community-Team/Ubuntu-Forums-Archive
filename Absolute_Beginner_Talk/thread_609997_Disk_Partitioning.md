---
title: "Disk Partitioning"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Skip Da Shu on 2007-11-11
Well since I haven't figured out how to back out the bad driver install yet... I may be starting over from scratch... I'd like to ask something about Disk Partitioning.

When I installed the first time I (from reading here) partitioned up the 10GB drive as follows:

1) EXT3, Primary, root, 5GB
2) swap, Logical, swap, 1GB
3) EXT3, Logical, home, 4GB

After all was said and done I saw very little that ended up in /home

It seems my main application I want on this machine (BOINC) ended up in /ect directories.

If I reinstall I am inclined to set up two partitions:

1) EXT3, Primary, root, 9GB
2) swap, logical, swap, 1GB or less

Any thoughts on this?

---

### Post by kshane on 2007-11-11
the two partition setup looks good to me.  Why one gb partition?  How much ram?

Kevin

---

### Post by Skip Da Shu on 2007-11-11
> **kshane said:**
> the two partition setup looks good to me.  Why one gb partition?  How much ram?

Kevin

single 512MB stick CAS 2.5

---

