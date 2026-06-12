---
title: "[SOLVED] Partition won't unmount"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-07-05
Ok... so I'm trying to delete an NTFS partition... I'm using GParted, but the Partition simply won't unmount! And so I can't delete it...

Any ideas? GParted tells me it can't find the mount point, but I can read/write to it (using ntfs-3g).

Thanks in advance.

---

### Post by bodhi.zazen on 2007-07-05
1. Go to System > Preferences > Removable Drives and Media and uncheck the box about automatically mounting drives.

2. Run gparted as root. ```
gksudo gparted
```

---

### Post by sab0403 on 2007-07-10
Actually the solution was to boot with the LiveCD, since the physical disk I wanted to repartition was my only disk (hence, its root partition couldn't be unmounted nor worked on). I then used GParted from the LiveCD, and everything worked fine.

Thanks again!

---

