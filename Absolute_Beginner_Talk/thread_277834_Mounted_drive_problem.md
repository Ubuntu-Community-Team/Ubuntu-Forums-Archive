---
title: "Mounted drive problem"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Nirc on 2006-10-15
I have recently added a new partition to my pc and mounted it in linux, and now mounted drives do not appear as icons on my computer. I can access them if I goto /media/drivename. I have edited fstab with the new entry: /dev/hdb2       /media/linuxswap  vfat    iocharset=utf8,umask=000   0       0. I followed the instructions here [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) to mount the hdd and now I can't even see the drives I had before..

---

### Post by taurus on 2006-10-15
What's the output of this command from a terminal?

```
df -h
```

---

