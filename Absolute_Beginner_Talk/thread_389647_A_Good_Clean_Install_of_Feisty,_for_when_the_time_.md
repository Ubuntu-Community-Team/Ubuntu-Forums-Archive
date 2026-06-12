---
title: "A Good Clean Install of Feisty, for when the time comes."
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-03-21
I'm planning to do a few things when Feisty comes out that I didn't know enough to do when I started using Dapper and Edgy.

-create a /home partition,
-dual boot windows xp

etc, etc.

I was wondering if there's any other good ideas or tips you could give me for the pre-install and install itself that will leave me with a faster, more efficient system than before.

---

### Post by cowlip on 2007-03-21
Perhaps you could try a software RAID from the Ubuntu alternate install CD?  That way you should be able to pool hard drives and resize easily.  Have you decided whether to use a swap file or swap partition? (from what I understand, swap files only problem is lacking support for hibernation)

Some people also create a separate /var partition with a quota, but that's mostly servers so they don't kill the root filesystem with logs

---

### Post by sunexplodes on 2007-03-21
What's the difference between using a partition and a swap file, performance-wise?

---

