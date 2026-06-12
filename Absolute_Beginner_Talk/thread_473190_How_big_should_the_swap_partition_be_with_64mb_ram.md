---
title: "How big should the swap partition be with 64mb ram? (Xubuntu)"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Luigi239 on 2007-06-13
Hello all, I started installing xubuntu with 64mb of ram on my iMac g3. I figured I would need alot of swap, so I put in an 800mb swap file... something inside me is saying I put in way to much. Did I? How big should it be? Is there a way to re-size it without loosing all of my data?

Thanks.

---

### Post by bodhi.zazen on 2007-06-13
Most people would advise RAM X2

It will not hurt to have a larger swap, except for the HD space.

You can resize your partitions with Gparted, just unmount the partitions first

For swap : ```
swapoff /dev/hdxy
```

---

### Post by kerry_s on 2007-06-13
I always use 1gig(1024) if i have the space.

---

