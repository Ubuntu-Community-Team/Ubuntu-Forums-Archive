---
title: "reinstall multiboot"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-14
I have a SATA disk divided into sda1, sda2, sda3, sda4, sda5

sda1,2,3 are windows xp, vista32bit,vista64bit.

sda5 is the ubuntu partition & is the active partition. sda4 is linux swap.

I currently have feisty but would like to install either ubuntu gutsy or maybe kubuntu gutsy.

I will need to install from the alternate cd I think, because I have trouble with ati graphics otherwise.

should I be able to do this okay without damaging my existing windows installs?

Here's my /boot/grub/menu.list

```

 default        0 
timeout        10 

title        Ubuntu, kernel 2.6.20-16-generic 
root        (hd0,4) 
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-generic 
quiet 
savedefault 
 
title        Ubuntu, kernel 2.6.20-16-generic (recovery mode) 
root        (hd0,4) 
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro single 
initrd        /boot/initrd.img-2.6.20-16-generic 
 
title        Ubuntu, kernel 2.6.20-15-generic 
root        (hd0,4) 
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic 
quiet 
savedefault 
 
title        Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root        (hd0,4) 
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=6b9802a0-b3e3-460e-96b1-32a3eb95de1f ro single 
initrd        /boot/initrd.img-2.6.20-15-generic 
 
title        Ubuntu, memtest86+ 
root        (hd0,4) 
kernel        /boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
 
# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title        Other operating systems: 
root 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title        Windows Vista/Longhorn (loader) 
root        (hd0,0) 
savedefault 
makeactive 
chainloader    +1

```

I think the windows loader mentioned at the bottom of menu.list takes care of all 3 windows installs.

---

### Post by Crooksey on 2008-02-14
```

sudo apt-get update
sudo apt-get dist-upgrade
```

Whats wrong with that?

Also update your sources.list, search wiki for complete guide.

---

### Post by ecs_pf5 on 2008-02-14
Ah right :) thanks

That wouldn't let me try kubuntu though I take it..?

---

### Post by Crooksey on 2008-02-14
No, but the command below will

```

sudo apt-get install kubuntu-desktop
```

---

