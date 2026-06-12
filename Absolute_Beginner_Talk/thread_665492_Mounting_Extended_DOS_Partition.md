---
title: "Mounting Extended DOS Partition"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Ronco Pizatto on 2008-01-12
I popped the Ubuntu 7.10 CD into my desktop and ran it Live. Everything worked great except it did not show my Fat 32 Extended DOS partition which is D Drive containing all my data. Do I need to mount the drive? It is just a partition and not a separate hard drive. Any suggestions?

---

### Post by Cypher on 2008-01-12
In the Live CD, go to Applications->Accessories->Terminal and type
```

fdisk -l

```
This should list all hard drives and all partitions, look for the one that says FAT32/VFAT..and that's the partition you'd want to mount to get access to your data.

---

### Post by Ronco Pizatto on 2008-01-15
Thanks for the response. I followed your directions but the fdisk -l option did not list any partitions. The partition is there when I run Win2000 and it is a Fat 32. Any other ideas would be appreciated.

---

### Post by derouge on 2008-01-15
Can you at least post the output of "fdisk -l?" It would be very odd if nothing is being shown. You may have to be root.

```
sudo fdisk -l
```

(lower case L, not an I)

---

### Post by Ronco Pizatto on 2008-01-18
It is indeed very odd. Nothing was shown. No big deal though. I like Ubuntu and I'll just install it to my hard drive and see if it sees the partition then. Thanks for your comments.

---

