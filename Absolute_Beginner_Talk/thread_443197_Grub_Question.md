---
title: "Grub Question"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by an4rew on 2007-05-14
I have Ubuntu and XP in grub menu working fine but i want to install another distro, would grub automatically setup without messing with Ubuntu, XP?

---

### Post by Kobalt on 2007-05-14
Which distro are you planing to install ? 
Theorically, your newly installed grub would overwrite your existing one but detect your XP and Ubuntu install, add them to the list alongside your new distro... If it messes up anyway you can get grub reinstalled quite easily from a LiveCD. Just make sur you don't mess with your partitions and you'll keep your data safe.

---

### Post by tchoklat on 2007-05-14
from personal experience. Install the new OS with it's grub in it's root patrition - not in MBR as it will then write over your Ubuntu bootloader. Modify then your Ubuntu /boot/grub/menu.lst file to chain load the new OS.
 

Tony

---

### Post by geekphreak on 2007-05-14
Depends on the distro. First of all it needs to use grub and not, say, lilo. And most importantly, it needs to have good detection for other kernels installed. Some distros do, some don't. Make sure you back up your grub menu.lst before, just in case.

---

### Post by mattmole on 2007-05-14
In my experience I would say that as long as the distro has a reasonable tool for installing grub then you shouldn't have a problem.

In the past I had a machine with Windows, SUSE, Red Hat and Gentoo installed and they all worked together fine.

If you do find your distro does mess up the menu.lst file that grub uses, you should be able to boot into the distros by following one of many grub guides.

Mattmole

---

