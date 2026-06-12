---
title: "Linux :: compact flash"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by opscure on 2008-04-04
> i used the following grub.conf file :
========
default=0
timeout=10
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu
title Dyna-linux
root (hd0,0)
kernel /boot/vmlinuz-2.6.21-1.3194.fc7 rw root=/dev/sda1 init=/bin/sh
initrd /boot/initrd-2.6.21-1.3194.fc7.img



What device did you install your OS to?  hd or sda?

if it's sda1 then your grub.conf should probably look more like this

```
i used the following grub.conf file :
========
default=0
timeout=10
splashimage=(sda1,0)/boot/grub/splash.xpm.gz
hiddenmenu
title Dyna-linux
root (sda1,0)
kernel /boot/vmlinuz-2.6.21-1.3194.fc7 rw root=LABEL=/ 
initrd /boot/initrd-2.6.21-1.3194.fc7.img

```

Be sure to make a backups.  Let us know how you make out.

---

