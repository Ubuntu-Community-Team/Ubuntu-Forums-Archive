---
title: "grub"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by IISpII on 2007-11-10
how do i use gurb (or anything else) to boot two or more different distros?  I realy have no idea what im doing, so any help is appreciated. Thanks

---

### Post by init1 on 2007-11-10
> **IISpII said:**
> how do i use gurb (or anything else) to boot two or more different distros?  I realy have no idea what im doing, so any help is appreciated. Thanks
To add a distro to the grub menu, you need to edit the /boot/grub/menu.lst. From there, it all depends on the distro that you need to add. The general syntax is:
title The distro
root (hd0,0)
kernel /boot/vmlinuz root=/dev/hda1
initrd /boot/initrd.gz
boot
This, of course, will not boot anything. It's an example.

---

