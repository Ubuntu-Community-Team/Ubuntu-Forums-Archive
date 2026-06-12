---
title: "Xen on Ubuntu on Mac"
date: 2007-12-08
forum: Apple Intel Users
---

### Post by macbuntu_paul on 2007-12-08
hi,

i run ubuntu on my macbook 1st gen. now i want to use xen 3.1.
the installation succeeded.
in the /boot/grub/menu.lst i insert

```
title    Xen 3.1 / XenLinux 2.6
kernel   /boot/xen-3.1.0.gz dom0_mem=1048576 noreboot
module   /boot/vmlinuz-2.6.18-xen root=/dev/sda4 ro console=tty
```

if i want to boot the Xen3.1 then it reboots.
i think the problem is the he can't mount the root fs.
i got an error.
```
unknow block(0,0)
```

i hope anyone can help me!
thanks

---

### Post by cyberdork33 on 2007-12-09
do you not need to add a 'root' line to your menu.lst?

---

