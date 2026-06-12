---
title: "overlayfs after switch_root"
date: 2013-04-15
forum: Any Other OS
---

### Post by kacper on 2013-04-15
I'm trying to get overlayfs working. I patched the kernel and the overlay seems to work in initramfs but as soon as I issue switch_root I lose the overlay.

Here is my initramfs init:
```

#!/bin/busybox sh

# Mount the /proc and /sys filesystems.
mount -t proc none /proc
mount -t sysfs none /sys

echo "Welcome to BUSYBOX!"
mount -o ro /dev/mmcblk0p2 /mnt/root
mount -t tmpfs tmpfs /overlay
mount -t overlayfs overlayfs -o lowerdir=/mnt/root,upperdir=/overlay /mnt/ro

# Clean up.
#umount /proc
#umount /sys

exec switch_root /mnt/ro /sbin/init

```

*/mnt/root* and */overlay* are merged into */mnt/ro*. And it works right to the point where we make */mnt/ro* root. There seems to be very little information on overlayfs so I hope I can get some help here.

---

