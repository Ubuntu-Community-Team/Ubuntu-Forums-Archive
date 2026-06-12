---
title: "Is GRUB necessary if you have reFIt?"
date: 2008-11-23
forum: Apple Hardware Users
---

### Post by Jason Syn on 2008-11-23
Im getting ready to triple boot my macbook with Leopard, XP, And Ubuntu. When im installing Ubuntu is it necessary for me to install grub if i already have refit as my bootloader. Will Ubuntu still boot without it. Because it is annoying to go through the grub screen after you pick Linux Or Windows and pick the OS again.

Thanks

---

### Post by cyberdork33 on 2008-11-23
> **Jason Syn said:**
> Im getting ready to triple boot my macbook with Leopard, XP, And Ubuntu. When im installing Ubuntu is it necessary for me to install grub if i already have refit as my bootloader. Will Ubuntu still boot without it. Because it is annoying to go through the grub screen after you pick Linux Or Windows and pick the OS again.

Thanks

refit is not a bootloader it is just a pretty menu system. GRUB is the bootlaoder for Linux. You need it to load the Linux Kernel. You are not choosing what OS to start in GRUB, you are choosing what Kernel to load.

If you would like to not see GRUB so much (it will boot the first item by default if you select nothing) then you can adjust the timeout in the /boot/grub/menu.lst file. I wouldn't set it to zero though because then when you need to select to boot into recovery mode or something it makes it a little difficult.

---

