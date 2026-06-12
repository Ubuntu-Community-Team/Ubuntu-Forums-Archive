---
title: "dual boot xp gutsy partion scheme"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-08
Hello,

I have an 80 gig hard drive that I am trying to dual boot with xp and gutsy. I have left over 30 gigs for the linux install but when I am at the partition screen it doesn't provide me the option of installing on the 30 gigs that I left for it. What it does is try to get me to install on my secondary hard drive that I would like to be able to use for both computers. I know that I need to partion manually but I don't know exactly what is needed. Is a swap really necessary? Is the FAT32 part necessary?

Thanks

---

### Post by Rocket2DMn on 2008-01-08
That 30 gigs will have to be partitioned further.  You will need a partition for swap (of type swap) and a root partition to be mounted at "/" using the ext3 file system.  So yeah, swap is necessary, but what is this FAT32?  Is that another hard drive or partition?

---

