---
title: "Backup"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ajeffreys on 2007-06-11
How could I make a complete backup of ubuntu, so that I can reinstall everything once I have installed vista, without having to go online?

---

### Post by Skrynesaver on 2007-06-11
If you have already got a partition set aside for Vista you can make a perfect copy of you ubuntu install with dd
```

dd if=/dev/hda1 of=/media/backupdevice/ubuntu.bak

```
However why can't you just reinstall with your instalation media?

---

