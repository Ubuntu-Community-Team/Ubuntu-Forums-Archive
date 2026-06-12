---
title: "I made a mistake with partitions :("
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Mark1948 on 2007-06-08
I booted the install CD and got as far as the partitioning option, it offered to resize my 120GB boot drive and grab some space. I said OK and then it said it needed 43GB of space. At this point I wasn’t sure I had 43GB free so I rebooted and went back into XP to check the space.

After freeing more space I rebooted again and now when it gets to partitioning it says it can’t continue due to an unknown problem. It offered to do the partition changes first time but not now, any ideas why???

Cheers all

---

### Post by loserboy on 2007-06-08
I haven't encountered that same problem, but you probably need to just format the area thats having the issue through the manual partitioner

---

### Post by stchman on 2007-06-08
> **Mark1948 said:**
> I booted the install CD and got as far as the partitioning option, it offered to resize my 120GB boot drive and grab some space. I said OK and then it said it needed 43GB of space. At this point I wasn’t sure I had 43GB free so I rebooted and went back into XP to check the space.

After freeing more space I rebooted again and now when it gets to partitioning it says it can’t continue due to an unknown problem. It offered to do the partition changes first time but not now, any ideas why???

Cheers all

Best way to install Ubuntu IMO is to make some free space on your hard drive.  This can be accomplished easily if you have a partition that is doing nothing.  If your drive is all ONE big drive you will need to use gparted to resize your hdd main partition and leave the reast as free space.

Once this is done tell Ubuntu installer to use largest free space.

---

### Post by hummingbird59 on 2007-06-08
Maybe defrag and disk clean once or twice and try again?  Don't know for sure, but maybe worth a try. Good luck!

---

