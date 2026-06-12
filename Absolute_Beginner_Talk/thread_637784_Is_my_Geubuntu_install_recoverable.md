---
title: "Is my Geubuntu install recoverable?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by infoseeker on 2007-12-11
I installed Geubuntu (7.10) yesterday and was enjoying the experience, rebooted to Ubuntu (dual booting) once I was done, attempted to go back to Geubuntu now that I am back from work, and all I get is the following (more or less) on bootup (on normal AND recover):
> ...
...
Freeing unused kernel memory: 384k freed
Failed to execute /init
Kernel panic - not syncing: No init found. Try passing init= option to kernel.
Which, needless to say, requires a hardware reset to continue.
I remember doing an update and enabling Nvidia restricted drivers, but not much more than that.  All that I can get to work under the Geubuntu menu items is 'memtest' :D

Is there any hope of recovery, or is a reinstall in order?

---

### Post by gilgongo on 2007-12-11
How are you doing the dual boot? With grub, or something else?

---

### Post by infoseeker on 2007-12-12
Using Grub.  I even double-checked each line in menu.lst and nothing seems any different to the Ubuntu lines....using the same kernel as Ubuntu...only different partition.
Even changed the 'root=' format from 'uuid' to 'dev' but makes no difference.
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5c828450-cdd7-4dd8-a979-6afb4f48f00a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5c828450-cdd7-4dd8-a979-6afb4f48f00a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Geubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Geubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Geubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

```


EDIT : Finally made the decision to reinstall, and all seems happy so far.  Not figured out what exactly caused the problem.  Haven't done the updates yet tho :) other than those done during the install (security updates maybe?)

---

### Post by gilgongo on 2007-12-12
I suppose it's just possible you had a bad block on the HD in the boot sector or something. Might be worth booting from CD and running fsck on the disk.

---

