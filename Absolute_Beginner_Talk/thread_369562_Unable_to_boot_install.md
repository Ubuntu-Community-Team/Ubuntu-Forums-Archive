---
title: "Unable to boot install"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Ryguy085 on 2007-02-24
So I've now installed ubuntu 6.06 using the live cd in graphics safe mode. Now whenever I boot up my computer the boot process stalls at mounting root filesystem and then drops into the shell. I am then informed that /dev/hde1/ does not exist. I am installing ubuntu to the master ide hdd by itself if that helps at all. If someone could help me on this I would be most appreciative. Thank you.

---

### Post by taurus on 2007-02-24
Can you post the output of these two commands?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Ryguy085 on 2007-02-24
```

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        9351    75111876   83  Linux
/dev/hde2            9352        9729     3036285    5  Extended
/dev/hde5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       24792   199141708+   7  HPFS/NTFS

```

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

---

