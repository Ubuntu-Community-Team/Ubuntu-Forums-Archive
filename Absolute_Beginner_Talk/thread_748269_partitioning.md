---
title: "partitioning"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by tmjohn403 on 2008-04-07
[B]partioning

I,m trying to load ubuntu to a clean hard drive and when it gets to page 4 it asks "how do you want to partition the disk. The only option it gives me is manual, no guided . I click to forward and get a page that says "prepare disk space prepare partitions" but it won't let me enter any information and now I,m stuck as it won't let me go forward. Any Ideas:


Thanks
__________________

---

### Post by neurostu on 2008-04-07
One thing you might try is to boot the live cd. Then open GParted under System->Administration-->Partition Editor

Create 2 partitions.  Format the first as EXT3 and set its mount point as /

Create a second partition and set its mount point as swap. Set the size of this partition from 1 to 2 gbs.

After these operations are done reboot the live cd and try to install.

---

### Post by Duck2006 on 2008-04-07
You can try a live cd of parted magic to partition your drive, and then boot to the live cd of ubuntu to install it.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

