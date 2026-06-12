---
title: "Lost 20 gig to formatting?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-09-27
My hard disk says it can store 320 gig, but looking at gparted my main partition is just under 300 gig and the swap is 1 gig. Is this normal or is there something funny going on?

I'm using ext3

---

### Post by luisromangz on 2007-09-27
Manufacturers usually label their hard disks using the metric units, not binary units, so in a 300GB (in metric units) there are only 292GB (binary units). For example: 1 K (metric) = 1000, 1K(binary) 1024. I think that this is what is happening with your HD.

---

### Post by ThrobbingBrain66 on 2007-09-27
ext3 reserves 5% of your disk by default for privilaged processes to run to avoid fragmentation.  To regain some of your space, use the tune2fs command:

```
sudo tune2fs -m 2 /dev/sda1
```

Assuming your drive is at /dev/sda1, this command reserves 2% of your drive instead of 5%.  If the drive is just for media or things like that you can probably set it to zero, otherwise I wouldn't go less than 1-2%

---

