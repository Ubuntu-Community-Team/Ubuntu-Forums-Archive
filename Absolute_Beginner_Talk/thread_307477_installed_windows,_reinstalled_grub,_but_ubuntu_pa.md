---
title: "installed windows, reinstalled grub, but ubuntu partitions won't mount"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by smegmaster on 2006-11-26
The title pretty much says it all. I installed Windows on a free partition, which I followed by reinstalling grub from the Edgy Live CD. However, when I try to load Ubuntu from grub, I get an error 17. 

When I run ```
sudo fdisk -l
``` here's the result:

```

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               5         131     1020127+  82  Linux swap / Solaris
/dev/hda2             132        3573    27647865   83  Linux
/dev/hda3   *        3574        4864    10369957+   7  HPFS/NTFS

```

When I try to fix this by opening grub and doing ```

root (hd0,2)
setup (hd0)

```

I also get an error 17.

Can anyone help? I'm pretty lost here. I've never had this problem before.

Thanks.

---

### Post by LLRNR on 2006-11-26
Did you follow [this](http://www.ubuntuforums.org/showthread.php?t=224351) guide? It seems... clear, accurate and trustworthy.

LLRNR

---

### Post by smegmaster on 2006-11-26
I tried that. All the steps went through, but after I rebooted I got the same error. Also, hsa3 is still starred as boot when I do fdisk -l.

---

