---
title: "Boot time problems with dapper"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by p1r0 on 2006-06-04
When Ubuntu boots up at the ```
Checking all file systems
``` point goes out of the nice orange style and in plain console like black and white screen says ```
There are differences between the boot sector and its backup 
``` and then something like ```
Not automatically fixing this
```

The thing that does it seems to be a dosfsck application and in fact the problem is only for my fat32 partitions. I scanned them using window$ scandisk and they have no errors.

Any ideas???](*,)

---

### Post by uzi09 on 2006-06-04
try running in rescue mode (select rescue mode from grub menu) and as root (which should be defaulted) run:

```
fsck
```

---

