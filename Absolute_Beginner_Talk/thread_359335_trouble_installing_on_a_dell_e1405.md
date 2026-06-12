---
title: "trouble installing on a dell e1405"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by rth92 on 2007-02-11
hi,

i am completly new to linux, but i saw ubuntu and decided that i wanted to try it, but i still want to keep XP. i have Acronis disk director suite and i used it to partition my hard drive and gave 2 gigs to swap and 18 to ubuntu and i set it for ext3. mabye that could be a mistake? anyway, i can get into ubuntu (edgy) fine, after i bypass the X thing... when i go to install it, i assign the root / to the 18 gig partition and the swap to the 2 gig partition, like i said before. then when i click install it says something like "no root partition assigned." any help with this is GREATLY APPRECIATED!!

thanks

---

### Post by confused57 on 2007-02-11
> **rth92 said:**
> hi,

i am completly new to linux, but i saw ubuntu and decided that i wanted to try it, but i still want to keep XP. i have Acronis disk director suite and i used it to partition my hard drive and gave 2 gigs to swap and 18 to ubuntu and i set it for ext3. mabye that could be a mistake? anyway, i can get into ubuntu (edgy) fine, after i bypass the X thing... when i go to install it, i assign the root / to the 18 gig partition and the swap to the 2 gig partition, like i said before. then when i click install it says something like "no root partition assigned." any help with this is GREATLY APPRECIATED!!

thanks

You would probably have better luck pre-formatting the paritions with a Linux partitioner, such as the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by rth92 on 2007-02-11
would that wipe out everything on my hard drive though?

---

### Post by nickoli_02 on 2007-02-12
No, the partitioner on the ubuntu install CD will not wipe everything from your drive. You can keep XP and only touch the partition you created for ubuntu.

---

### Post by rth92 on 2007-02-12
great, but when im in ubuntu's partitioner, it does not detect any other partitions -- it just says unallocated space..........

---

