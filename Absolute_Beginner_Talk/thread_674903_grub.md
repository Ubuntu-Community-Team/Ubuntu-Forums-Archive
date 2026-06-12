---
title: "grub?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by f0olyc0oly on 2008-01-22
what's a grub? do i actually need it in order for me to install ubuntu to a two different hard disk?:confused:

---

### Post by Cypher on 2008-01-22
GRUB is the bootloader for Linux. It allows you to boot into Linux and other OS' (like Windows). It is installed by default when you install Linux. 

Windows also has a boot loader, but since there is only one option (boot Windows), the menu is hidden. Traditionally when people want to Dual-boot Windows and Linux, you install Windows first and then install Linux and GRUB will detect Windows and make it an option in the menu alongside Linux.

GRUB replaced LILO (Linux Loader) which was the older boot loader. LILO was a little more rigid in it's way than GRUB which is a lot more flexible, especially for making changes on the fly..

---

### Post by stump138 on 2008-01-22
Grub stands for Grand Unified Bootloader.  If you plan on having multiple operating systems in your computer such as *cough* windows *cough* or something like that you need a utility such as grub to allow you to choose which OS you wish to use for the session.  Basic information on Grub can be found [here]("http://www.gnu.org/software/grub") :)

---

