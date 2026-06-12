---
title: "Lost GB when formating"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-17
I have format my harddrive 500 GB with Gparted live-cd. I choose filesystem ext2 and when the process was ready I run command df and I notice that size of harddrive is 459 GB, used is 73 MB and available of harddrive is 436 GB. How does it come that 23 GB (459-436=23) is lost that I cant use when command df shows that only 73 MB is used?

---

### Post by mcduck on 2007-02-17
by default 5% of disk space on Ext partitions is reserved for root user only. And also remember the difference between disk sizes reported by disk manufacturers and disk sizes as computers see them..

edit: Disk manufactures calculate sizes like 1000KB=1MB ( so 1GB is 1000000000 Bytes), but your computer really sees it like 1024KB=1MB (1GB is 1073741824 Bytes)..

---

### Post by inspiron on 2007-02-17
> **mcduck said:**
> by default 5% of disk space on Ext partitions is reserved for root user only. And also remember the difference between disk sizes reported by disk manufacturers and disk sizes as computers see them..

edit: Disk manufactures calculate sizes like 1000KB=1MB ( so 1GB is 1000000000 Bytes), but your computer really sees it like 1024KB=1MB (1GB is 1073741824 Bytes)..

Thank you, that information about that 5% of disk space on Ext partitions is reserved for root user only explained it.

---

### Post by mcduck on 2007-02-17
by the way, if the disk is not your / partition but some extra storage instead, you can set the reserved space to 0% with the following command:

```
sudo tune2fs -m 0 /dev/<yourpartition>
```
replace <yourpartition> with right one of course ;)

---

### Post by jawwad on 2007-02-17
i have the same problem : what i can do ?

---

