---
title: "how to mount partition at startup"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by charlescarroll1 on 2007-12-31
I keep my media on a seperate partition.  Is there a way that I can make Ubuntu autmatically mount this partition at startup instead of doing it manually and typing in a pw every time?  The partition is NTFS is that helps.  Thanks.

---

### Post by Majorix on 2007-12-31
You have to edit /etc/fstab.
```
gksudo gedit /etc/fstab
```
Google for info on what you have to add in there.

---

### Post by spiderbatdad on 2007-12-31
[http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)

---

### Post by taurus on 2007-12-31
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

