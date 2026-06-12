---
title: "How to add boot options ??"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by MDMS on 2008-04-08
Hi everyone.

I've just installed Xubuntu 7.1 on an old IBM 380Z and I think I need to add the boot option "acpi=force" and possibly some others.

So my question is:  Where and How to I permanently add such a boot option?

Thanks!

---

### Post by sisco311 on 2008-04-08
open a terminal:

Applications -> Accessories -> Terminal

and type:
```
gksu mousepad /boot/grub/menu.lst
```to edit the grub configuration file. 

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
** kernel          /boot/vmlinuz-2.6.22-14-generic** [B]root=UUID=xxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx ro quiet splash
[/B]initrd          /boot/initrd.img-2.6.22-14-generic
quiet
--->

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
** kernel          /boot/vmlinuz-2.6.22-14-generic** **root=UUID=xxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx ro quiet splash *acpi=force***
initrd          /boot/initrd.img-2.6.22-14-generic
quiet


---

### Post by MDMS on 2008-04-08
Works!  Thanks.

---

### Post by plucky on 2008-04-08
Also add it > ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash [color=red]acpi=force[/color] here in the same file so that it is added by default when grub is updated.


Good Luck

---

