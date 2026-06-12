---
title: "Help re-sizing hda3(/)"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by wastedfluid on 2007-07-03
Hi guys.

I've gone full time with Ubuntu.  I have removed hda1+hda2(recovery+windows xp partitions).  They were 34gb combined.

So, I have hda3, hda4, and hda5.  Hda4+hda5=extended+logical partitions for swap.  Hda3 = /.

I have 35gb BEFORE "/" (hda3)

How do I safely add it to hda3?  I tried booting in live and trying to add it that way.. but apparently, you can only add space after a partition, not from unallocated spaec located before it.

I've attached a screenshot.  Thanks!

---

### Post by jose_ramirez on 2007-07-03
Hi,

Your root partition is pretty big... I have never resize the root partition but maybe an approach for you can be to define a new partition of 34 GB and mount /home in the new partition. I like this approach because you can separate the operating system from the user's files.

Regards,

-Jose

---

### Post by louieb on 2007-07-03
the easiest thing to do (also the safest) in your case you can make the unallocated space a primary partition. just format it ext3 and once your done go to system>adnim>disks and make it available for use. Having a separate data partition is a safe and sane way to go.

---

