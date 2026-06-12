---
title: "mkdosfs not formatting my partition?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Yes on 2008-02-16
I'm running [Tomsrtbt](http://www.toms.net/rb/) off of a floppy and trying to format the partition to FAT32 with the command 'mkdosfs -v -F32 /dev/hda1'.

When I run that, it says:

```
/dev/hda1 has 16 heads and 52 sectors per track,
using oxf8 media descriptor, with 91468 sectors;
file system has 2 32-bit FATs and 1 sector per cluster.
FAT size is 709 sectors, and provides 90727 clusters.
Volume ID is 4496dd6b, no volume label.
```

Then according to fdisk the filesystem hasn't changed.  So does anyone know what that all means/why it's not formatting?

Thanks.

---

### Post by dstew on 2008-02-16
Are you trying to format the floppy? I don't think you can format a floppy with FAT32, only FAT16. If you are trying to format a hard disk partition, which it seems you are, maybe you need to be root:```
sudo mkdosfs -v -F32 /dev/hda1
```EDIT: That Tomsrtbt looks pretty cool.

---

