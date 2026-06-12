---
title: "how to disable automounting partitions?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-02-21
How to disable automounting (on boot) the partitions other than Ubuntu-partition?

---

### Post by taurus on 2007-02-21
Just put a # in front of the entry you don't want to mount at boot in /etc/fstab.

```
gksudo gedit /etc/fstab
```

---

