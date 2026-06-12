---
title: "/home on a seperate partition"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-05-20
After going through the virtues of putting /home on a separate partition I did exactly that, but was just wondering that when you reinstall a new system, how do you handle correctly the separate home partition?

---

### Post by Kobalt on 2007-05-20
When you will install your new system, you will go into something like 'Advanced' or 'Manual' partitioning. From there, you'll select the partition on which your system is/was installed and your swap partition and give them a mount point, being respectively / and swap. Do the same for you /home partition but make sure not to select the format option for this one, so that you keep all you settings and files.

---

