---
title: "Can 2 Hard drives be mounted on same mounting point?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by iffy9 on 2006-03-28
I have a pc with 3 hard drives installed.  The small 10GB drive has Ubuntu installed.  I want to use a 20GB and 40GB drives as a file server for the rest of the family.  The subject says it all really, can I mount both the 20GB (/dev/hdb1) and 40GB (/dev/hdd) on the same mounting point, so it appears as a big 60GB drive?

TIA

Ian

---

### Post by Ubuntuud on 2006-03-28
You'll probaly need to use LVM, but I don't know anything about it... (except that it makes 2 disks act as one)

---

### Post by ubuntuuser on 2006-03-28
You **can** mount two drives using the same mount point without getting any error messages, but linux will only access the drive mounted last. The other one will simply "disappear" until you unmount the second drive. LVM is what you need.

---

