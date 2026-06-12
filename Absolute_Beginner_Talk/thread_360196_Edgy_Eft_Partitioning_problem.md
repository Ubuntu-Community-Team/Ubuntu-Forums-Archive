---
title: "Edgy Eft Partitioning problem"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by rrand on 2007-02-12
Hi,

Trying (as a newbie) to install Edgy Eft from CD as a dual Windows boot and have gotten as far as partioning mount points.  I have all partitions listed and the mounts specified but when I click on the Forward button all I get is message !No root file system.  What does this mean pls?

---

### Post by phiphedog on 2007-02-12
You need to assign a partition to mount the root file system on.

Maybe this will help you
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by rrand on 2007-02-12
Tks for the suggestion - I had that specified ok but since my post I did a search on Google and found the cause was incorrect partions' file system spec.  As it was the ext3 was missing on the new ones I had created (it said 'unknown' - not sure why) so I deleted and recreated them all and now it is installing...

---

