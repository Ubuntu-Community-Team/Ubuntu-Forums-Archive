---
title: "Imac Partitioning HELP!"
date: 2007-07-15
forum: Apple PPC Users
---

### Post by wimpytx on 2007-07-15
I need to know how to partition my imac g3 so I can install ubuntu feisty fawn. Im not trying to partition it for two OS's, Just feisty but my root partition has to be 7gb to boot from. I have a 60gb hd. Does anyone know the partition scheme for this.

Thanks

---

### Post by czechman86 on 2007-07-15
i would just let linux do the partitioning and not use the manual, because you are using the entire drive for one os.

---

### Post by ssam on 2007-07-15
7gb for / and the rest for /home should work fine.

---

### Post by wimpytx on 2007-07-15
I tried doing that but it said problem mounting ext3 which is /home i have no idea what im doing :confused:

---

### Post by 0graham0 on 2007-07-15
I'm not that experienced but here's my two cents...

I had problems partitioning, until I opened the Partition Manager on the Live CD and created 3 partitions prior to install:

-One partition for swap,  formatted as swap (I made a 1 GB swap), a partition for boot partitioned under the ext2 file system (16 MB) and the final partition for root formatted as free space, the installer takes care of formatting it i think...?

I pieced that together from various sites on the internet when I was trying to install...these pages might shed some more light on the situation if you haven't checked them out yet:

[https://help.ubuntu.com/7.04/installation-guide/powerpc/partitioning.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/partitioning.html)
[https://help.ubuntu.com/7.04/installation-guide/powerpc/module-details.html#partman](https://help.ubuntu.com/7.04/installation-guide/powerpc/module-details.html#partman)

good luck

---

### Post by ssam on 2007-07-16
use ext3, this is the default choice. some people will recommend other file systems as being faster, but ext3 is very stable and well tested, and will give you less trouble.

are you using the live cd installer or the alternate text based installer?

---

### Post by wimpytx on 2007-07-18
live cd

---

### Post by wimpytx on 2007-08-21
i just bout an external hd enclosure and used my old hd as the boot.

---

