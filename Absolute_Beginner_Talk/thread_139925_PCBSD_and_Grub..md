---
title: "PCBSD and Grub."
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-03-05
As the name almost clearly spells out, I installed PCBSD, without the BSD boot loader, because I knew GRUB could handle it. Question is, how do I edit the menu.lst to allow PCBSD to boot?

Thanks

---

### Post by Pragmatist on 2006-03-05
From the GRUB manual: [http://www.gnu.org/software/grub/manual/grub.html#FreeBSD](http://www.gnu.org/software/grub/manual/grub.html#FreeBSD)
> 
4.2.3 FreeBSD

GRUB can load the kernel directly, either in ELF or a.out format. But this is not recommended, since FreeBSD's bootstrap interface sometimes changes heavily, so GRUB can't guarantee to pass kernel parameters correctly.

Thus, we'd recommend loading the very flexible loader /boot/loader instead. See this example:

     grub> root (hd0,a)
     grub> kernel /boot/loader
     grub> boot


---

