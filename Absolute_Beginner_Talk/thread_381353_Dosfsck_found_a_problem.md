---
title: "Dosfsck found a problem"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-03-10
Dosfsck found that one vfat partition has more clusters than space for them.

Here is the results of running dosfsck
```
sudo dosfsck -r /dev/hdc9
Password:
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
No FSINFO sector
1) Create one
2) Do without FSINFO
? 2
File system has 560128 clusters but only space for 560126 FAT entries.
```

It's not offering to fix it in interactive mode. It just reports the problem. I haven't tried automatic mode (something I don't like to do is let the system mess with the file system automatically). I've not had any problems but would like to correct the cluster count. Scandisk in W98 doesn't report this issue. 

Also, what are the pros and cons of creating a FSINFO sector?

---

### Post by Patrick K on 2007-03-19
Bump

---

### Post by Patrick K on 2007-04-27
bump

---

### Post by Cypher on 2007-04-27
Uh..did you just say Windows 98? :)

If Win98 has no problem with it, why are you messing with the partition again?

---

### Post by Patrick K on 2007-04-27
Because fsck gives this error> File system has 560128 clusters but only space for 560126 FAT entries
W98 doesn't see this but fsck does. Why is this?

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by Patrick K on 2007-05-02
bump

---

