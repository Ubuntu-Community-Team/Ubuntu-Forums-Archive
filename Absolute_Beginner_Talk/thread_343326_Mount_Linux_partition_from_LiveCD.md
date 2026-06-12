---
title: "Mount Linux partition from LiveCD"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by dyrer on 2007-01-21
Hello
How can mount linux partition from LiveCD
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       35724   286952998+  83  Linux
/dev/sdb2           35725       36481     6080602+   5  Extended
/dev/sdb5           35725       36481     6080571   82  Linux swap / Solaris

sudo mount /dev/sdb1 gives me
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by taurus on 2007-01-21
```
sudo mkdir /mnt/ubuntu
sudo mout -t ext3 /dev/sdb1 /mnt/ubuntu
df -h
```

---

### Post by Jussi01 on 2007-01-21
> **taurus said:**
> ```
sudo mkdir /mnt/ubuntu
sudo **mount** -t ext3 /dev/sdb1 /mnt/ubuntu
df -h
```


Think maybe there is a slight typo... mout=mount

---

