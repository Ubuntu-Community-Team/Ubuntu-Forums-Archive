---
title: "Help installing on Mac Mini?"
date: 2006-12-16
forum: Apple PPC Users
---

### Post by frenchbuntu on 2006-12-16
Hi

I've used Linux for over 2 years and decided to convince my brother, who has a powerpc mac mini, to dual boot.

Launching the live cd perfectly works, I have partitioned correctly (30 gigs Mac OSX, 9 gigs ext3, 1 gig swap).  When I try to install, it complains about "New World Boot partitions" not being mounted properly.  What should I mount, and where?

Thanks,
Henry

---

### Post by stream303 on 2006-12-16
The easiest way would be to delete your existing ext3 and swap partitons, then go back and instruct the installer to use "free space".  It will automatically take care of the new world boot partition for you.

---

### Post by frenchbuntu on 2006-12-17
Great idea.  Thanks.

---

