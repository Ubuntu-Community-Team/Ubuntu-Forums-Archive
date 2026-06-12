---
title: "HFS+ read only?"
date: 2010-11-30
forum: Apple Hardware Users
---

### Post by TechieJustin on 2010-11-30
Hi folks.  I'm trying to enable HFS+ read & write.  I formatted an external drive on my Mac to HFS+ non journalised.
When I try to copy stuff to the drive - permission denied.
I saw that somebody else had a similar problem so I tried to run fsck.hfsutils
```
~$ fsck.hfsplus /dev/sdb
Can't open /dev/sdb: Permission denied
```
What am I doing wrong?

---

### Post by conundrumx on 2010-11-30
You need to use sudo to elevate your privileges for most low level disk operations.

Type just "mount" and let's see if the disk is mounted properly.

More importantly, on a disk that size you should just be using FAT.

---

