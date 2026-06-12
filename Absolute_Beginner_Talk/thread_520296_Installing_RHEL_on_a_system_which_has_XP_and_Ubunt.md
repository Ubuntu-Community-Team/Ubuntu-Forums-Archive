---
title: "Installing RHEL on a system which has XP and Ubuntu"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by philipho on 2007-08-08
Hi all,

My system currently has 2 os installed, XP and Ubuntu. Upon booting up, i will be able to choose to load either os using GRUB.

I am planning to further install red hat enterprise linux, do i just install from the cd and GRUB will be autoconfigured to load 3 os or manual configuration is needed?

---

### Post by e_james on 2007-08-08
My shuttle had 3 OSs installed in the order XP, Ubuntu 6.06 and KnoppMyth. No problem with grub that I remember. When I upgraded Ubuntu 6.06 to 7.04 by reformatting the partitions for '/' and '/boot' the grub menu was incorrectly configured. It wants to boot from '/' rather than '/boot'. I edited the menu to fix this, but it goes back to the wrong setting when I download a new kernel. I suspect a bug in the 7.04 installer.

---

