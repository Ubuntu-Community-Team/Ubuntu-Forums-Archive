---
title: "Deleting OS X"
date: 2008-09-06
forum: Apple Hardware Users
---

### Post by Qloor on 2008-09-06
How would I go about deleting OS X from my MacBook entirely? I never use OS X and I want the extra space on my MacBook. I can't load OS X, though, so I need to know how to do it strictly from Ubuntu or another computer.

EDIT: Or, if possible, how could I boot my OS X files up? It doesn't work when I boot up and hold down Option/Alt. I don't want a new OS X, just some of my old files (which I failed to back up). Thanks in advance.

---

### Post by schauerlich on 2008-09-07
If you can't load into OS X, you may have already erased that partition, although it's possible you only erased the EFI partition. Could you post the output of this command?
```

fdisk -l

```

---

### Post by Qloor on 2008-09-07
> **EDavidBurg said:**
> If you can't load into OS X, you may have already erased that partition, although it's possible you only erased the EFI partition. Could you post the output of this command?
```

fdisk -l

```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003e78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18713   150312141   83  Linux
/dev/sda2           18714       19457     5976180    5  Extended
/dev/sda5           18714       19457     5976148+  82  Linux swap / Solaris
```

---

### Post by schauerlich on 2008-09-07
You appear to have already deleted OS X and anything else you had on those partitions.

---

### Post by Qloor on 2008-09-07
> **EDavidBurg said:**
> You appear to have already deleted OS X and anything else you had on those partitions.

Appears your right. Thanks!

---

### Post by cyberdork33 on 2008-09-07
> **Qloor said:**
> Appears your right. Thanks!

ok try this one:
```
sudo parted /dev/sda print
```

---

