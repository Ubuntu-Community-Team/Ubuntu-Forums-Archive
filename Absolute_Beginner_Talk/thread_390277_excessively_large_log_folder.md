---
title: "excessively large log folder"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by todizzle91 on 2007-03-21
I noticed that my free space quickly shrunk a few days after installing Ubuntu 6.10. Using the Disk Usage Analyzer, I saw that approximately 45gb was used for logs. Is there any way to reduce their size?

---

### Post by taurus on 2007-03-21
You can remove the old ones in /var/log.

<Alt>F2
```
gksudo nautilus
```
will give you a filemanager with root privilege so just navigate to /var/log and remove the backups.  Then, don't forget to empty your trash bin or they still take up the space.

---

### Post by mcduck on 2007-03-21
If the logs grow that big there is most likely some problem that causes some log file to fill with errors. Before deleting the logs you should check which one is growing and what is the error (and try to fix it). Otherwise you'll soon have the same problem again..

---

