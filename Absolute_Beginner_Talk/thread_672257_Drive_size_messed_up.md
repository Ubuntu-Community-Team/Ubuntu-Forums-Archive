---
title: "Drive size messed up"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by prann on 2008-01-19
I used Clonezilla to backup my 10gig Ubuntu hard drive to an external drive. The image was about 5gig which is right. Then took out the 10gig drive and replaced it with a 20gig. I made  1 partition and formated to ext3. Then restored the backup image to the new drive without the partition info, so I would have all 20gig on 1 partition. Now Disk Usage Analyzer reports total file capacity is 9gig, used 5.5gig, 3.5gig free. This would seem like I had the old drive in. And Gparted reports hbd1 size 18.1gig and 14.9gig used and 3.5gig free. How can I fix it so I can use all the space? One program said, can not save video, only 3.5gig free.

---

### Post by A4006 on 2008-01-20
Maybe you inadvertently copied over not only your backup but the 10 GB partition it was in.  You could try using gParted to merge any other partitions you have floating around, thus (hopefully) giving you your full HDD capacity.  It could also be that your drive is set to appear as smaller than it really is, which I don't know how to fix.

---

### Post by bwtranch on 2008-01-20
You didn't partition your drive right. Back up your system and read the docs.

---

### Post by prann on 2008-01-23
> **bwtranch said:**
> You didn't partition your drive right. Back up your system and read the docs.

I made the replacement drive 1 partition (whole drive) and then restored image without writing the partition info back (Clonezilla -k option). Seems like Ubuntu is fooled into thinking its the old 10gig size.

---

