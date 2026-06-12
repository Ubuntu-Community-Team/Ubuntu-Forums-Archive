---
title: "Partitions"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Shippou on 2008-02-23
Hello there!

Question: How do you change partition size without reformatting the partition?

My present state:
3GB - root
65 or more - Files Repository
maybe 1GB - swap

I want to do this:

4 to 5GB - root

without reformatting my Files Repository partition, or the root partition.

Files repository has currently 50.1GB free

I certainly don't want to reformat. 

Please help...

---

### Post by forestpixie on 2008-02-23
using gparted - either on the buntu cd or as a boot disc - resize files partition and then add the new  to the root drive, you won't need to reformat - but it'd be a good idea to have good backups

that assumes that the partitions are in root, files, swap order - check with 

```
sudo fdisk -l
```

---

