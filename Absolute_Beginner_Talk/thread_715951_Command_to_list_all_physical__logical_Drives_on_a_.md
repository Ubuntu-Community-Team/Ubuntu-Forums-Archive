---
title: "Command to list all physical / logical Drives on a machin"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-03-05
Hi,

Is there a command in Bash that will list all the drives.. logical / physical that are available?

I'm trying to determine which NTFS partition i need to mount...

Such as hda1, hdb2 etc

Thanks!

---

### Post by taurus on 2008-03-05
```
sudo fdisk -l
```

---

### Post by markbusu on 2008-03-05
Perfect Thanks!

---

