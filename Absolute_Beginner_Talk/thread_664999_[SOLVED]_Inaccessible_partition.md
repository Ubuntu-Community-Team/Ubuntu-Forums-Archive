---
title: "[SOLVED] Inaccessible partition"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by befana on 2008-01-11
Hi!
I do not know how and when, but actually I've made one of my partitions inaccessible to write on it. It is in ext3 format, and it is almost 20 GB. When installing Ubuntu 7.10 I've made three partitions - root, swap, and the third was home.  And now I can not write on the third partition. I've read here in this forum about ALT+F2 and gksudo nautilius, but it is obviously unsuitable for every day use, and for user like me (hwo does not understand much). And now I am wondering how to get access to this partition. On it is only a file (or folder?) Lost and Found. 
Any ideas how to get back my 20 GB?

---

### Post by taurus on 2008-01-11
You mean you mount the third partition as /home?

Can you post the outputs of these commands from a terminal?

```
sudo fdisl -l
cat /etc/fstab
df -h
```

---

### Post by befana on 2008-01-11
Wnen installing Ubuntu, I indicated to mount it as home. But now it is not my home partition. Why?

---

### Post by befana on 2008-01-11
After pressing Alt+F2 and "gksudo nautilus" I've chang&#1077;d root permissions and my permissions to create and delete files - they were only access files, and now I can write on sda6. So the problem is solved.

---

