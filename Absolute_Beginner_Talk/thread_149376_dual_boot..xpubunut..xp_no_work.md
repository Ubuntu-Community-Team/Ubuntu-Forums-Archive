---
title: "dual boot..xp/ubunut..xp no work"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by kbrown3074 on 2006-03-23
I attempted the separate disk dual boot..but to no avail.  I decided to install windows on first, then ubuntu.  XP did not show in the grub menu..I added it, but it still does not work.  I  used 'mount' to check the drives..its not being mounted.  How can I check what partition it is to hopefully change it correctly in the menu?

---

### Post by chuckyp on 2006-03-23
```

sudo fdisk -l

```
That will list your partitions.  You might have to specify a /dev/hda or /dev/hdb whatever hard disk but may not.

---

