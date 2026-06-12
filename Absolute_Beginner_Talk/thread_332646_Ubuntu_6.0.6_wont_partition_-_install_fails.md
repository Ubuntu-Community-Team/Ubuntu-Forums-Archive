---
title: "Ubuntu 6.0.6 wont partition - install fails"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by seasidedave on 2007-01-06
Win XP Home SP2.  160Gb maxtor, 133 Gb free. SCSI. Amd sempron 3300.  Live CD works fine so tried to install.  The partitioner fails to partition - says can't make space.  On quiting ubuntu live cd, I notice a message "raid monitor - failed".  Within windows I do have a utility (I don't know why!) called SiS raid.  But no raid is set up as I have only one hard drive!  The live cd is fine, I am sure because...
it installed perfectly on my old Amd 700 with 20Gb.:D 
I have a complete backup of c:\.  Windows will not partition the maxtor either.
I am not very technical so need easy to follow help please!

---

### Post by jvc26 on 2007-01-06
Have you defragged the harddrive? It may be that the filesystem is fragmented and so it cant set up a continuous partition and so the install wont go ahead. The raid thing is ok to ignore (if i remember rightly the same issue came up with my 6.06 - I think all it is doing is trying to turn off the raid stack, but since you havent got one it fails.) Hope that helps,
Il

---

### Post by seasidedave on 2007-01-06
> **Illuvator said:**
> Have you defragged the harddrive? It may be that the filesystem is fragmented and so it cant set up a continuous partition and so the install wont go ahead. The raid thing is ok to ignore (if i remember rightly the same issue came up with my 6.06 - I think all it is doing is trying to turn off the raid stack, but since you havent got one it fails.) Hope that helps,
Il
Yes I have defragged it.  There are no system problems at all either.  Oh yes, more spec if it helps - 1Gb RAM too, and even XP home works OK.  Though with and old AMD 700 running ubuntu better than Amd 3300 runs XP, I'd like to go Ubuntu and dual boot for a while.
Thanks for trying!

---

### Post by jvc26 on 2007-01-06
I almost might suggest wiping the lot and trying to install windows (in a partition of half the drive) and Ubuntu on one on the second half... But thats a pretty drastic idea, I'm afraid I'm not 100% sure of where to go from here - I'd hang fire a bit and you'll probs get a much better answer ;) :)
Il

---

