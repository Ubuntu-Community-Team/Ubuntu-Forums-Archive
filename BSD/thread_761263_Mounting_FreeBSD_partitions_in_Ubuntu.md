---
title: "Mounting FreeBSD partitions in Ubuntu"
date: 2008-04-21
forum: BSD
---

### Post by geeree on 2008-04-21
I have a dual-boot Dell Inspiron 640m laptop with Ubuntu 7.10 and FreeBSD 7.0. I want to mount all FreeBSD partitions (/, /home, /var, ...) in Ubuntu. Could someone please help?

"sudo fdisk -l /dev/sda" shows the following partition table:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d2e1d2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2617    21021021   a5  FreeBSD
/dev/sda3            2618        9337    53978400   83  Linux
/dev/sda4            9338        9729     3148740    f  W95 Ext'd (LBA)
/dev/sda5            9338        9599     2104483+   b  W95 FAT32
/dev/sda6            9600        9729     1044193+  82  Linux swap / Solaris

```

I tried the following to mount the FreeBSD "slice" /dev/sda1:

```

sudo mount -r -t ufs -o ufstype=ufs2 /dev/sda1/ /mnt

```

This worked, but I found that only the root partition of FreeBSD was mounted. I could not access the other partitions. How do I do that? (I am using the 2.6.22-14-generic kernel.)

Thanks,
Girish.

---

### Post by mips on 2008-04-21
I think it only mounts the 'slice' you need to mount each bsd partition in that slice individually.

[http://gentoo-wiki.com/HOWTO_Mount_UFS_partitions](http://gentoo-wiki.com/HOWTO_Mount_UFS_partitions)
[http://jovidman.wordpress.com/2008/02/23/howto-mount-ufs-partitions/](http://jovidman.wordpress.com/2008/02/23/howto-mount-ufs-partitions/)

---

### Post by geeree on 2008-04-22
> **mips said:**
> I think it only mounts the 'slice' you need to mount each bsd partition in that slice individually.

Thanks, mips. All I needed to say was "dmesg | grep 'bsd'"! The kernel didn't need recompilation, fortunately. But I then thought maybe I should recompile and see if I could bring in ufs read-write support. That isn't done yet though.

Thanks,
Girish.

---

