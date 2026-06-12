---
title: "Using Gparted to fix my external hdd.."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-10-29
I messed up and disconnected my hdd without unmounting.

I can see the hdd with Gparted. I need to fix it.

Does the Gparted check feature do this? If so, will I loose data?

---

### Post by tdrusk on 2007-10-29
bump

---

### Post by bodhi.zazen on 2007-10-29
Fixing it will depend on the filesystem ...

---

### Post by tdrusk on 2007-10-29
> **bodhi.zazen said:**
> Fixing it will depend on the filesystem ...
It's ext3

---

### Post by bodhi.zazen on 2007-10-29
Unmount the partition ...

Open a terminal 

run this command :```
sudo fsck -y /dev/sdxx
```

where "dev/sdxx" is the partition to be repaired.

---

### Post by tdrusk on 2007-10-29
okay that works :)

How can I get it to automount?

---

### Post by tdrusk on 2007-10-29
ah I fixed it

awesome.

---

