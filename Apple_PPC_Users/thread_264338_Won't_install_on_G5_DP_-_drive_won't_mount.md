---
title: "Won't install on G5 DP - drive won't mount?"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by chris_looney on 2006-09-24
I have 2 drives in my G5.  I can get info on one (10.4.7) and the other hard drive appears (10.3.9), but I cannot see any info about it.  10.3.9 has been partitioned into 2.  The first partition has 10.3.9 and is 91GB.  The second partition is for Ubuntu.  It is 94GB.  I tried using the largest continuous space and it gets to Detecting file systems...  (15%) and stops.  

Is it because the second drive I want to use for install is not mounted?  I found a posting saying to use the command

sudo mount -t hfsplus/dev/sdaX/mount/point

How do I get to the terminal in Linux?
Is this the best way to do a hard drive with 2 operating systems?  I want to be able to boot into 10.4.7, 10.3.9 and Ubuntu.

Thanks,
Chris

---

