---
title: "how to write in windows FS?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by paolo17 on 2006-12-05
hi im dual booting ubuntu 6.06 with windows xp, im wondering if there is a way for my ubuntu to be able to have write permission in my windows partition, all i can do is access my windows partition and get file from it, but what i would like is to be able to write files in it from my ubuntu, is it possible? my filesystem in windows is ntfs my ubuntu is ext3 (i think?). thanks people im a newbie so pls be kind. thanks.

---

### Post by yabbadabbadont on 2006-12-05
NTFS write support is experimental/limited/prone to errors.  There are windows drivers that allow you to access your ext2/3 partitions though that seem to work well.  Your most reliable option would be to create a fat32 partition (assuming that you have the space available) and use it to store files that you wish to share between Windows and Ubuntu.

---

