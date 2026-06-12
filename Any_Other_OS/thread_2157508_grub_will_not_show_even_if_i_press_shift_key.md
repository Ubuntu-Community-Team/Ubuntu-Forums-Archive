---
title: "grub will not show even if i press shift key"
date: 2013-06-25
forum: Any Other OS
---

### Post by syberhunter on 2013-06-25
I have done many installs and this has never happened before, on my friends machine with a fresh install of win 7 pro i installed Linux Mint 15 Cinnamon, after the install and reboot it went straight into Linux Mint, no grub menu. tried again, same thing. Tried holding shift while booting got a message saying Grub is loading, but didn't load, went straight to Mint again. Did a bit or research on how to configure Grub to show and then checked the installed Mint versions grub config in the terminal and it is all properly commented out and should be visible..anyone seen this before?

---

### Post by grahammechanical on 2013-06-25
When you run sudo update-grub does the terminal print show that os-prober is detecting Windows 7? As a wild guess are you holding down right shift? That is the one to hold down. When you look into /boot/grub/grub.cfg do you see any parameters for loading Windows?

Boot repair may help

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by sisco311 on 2013-06-25
Thread moved to **Other OS/Distro Support**.

---

### Post by ajgreeny on 2013-06-25
On my machine shift does not help to show the grub menu either; I have to repeat press and release Esc instead and then grub menu pops up.

I have a system with just Xubuntu 12.04 64bit on a system using UEFI instead of legacy BIOS,and GPT partitions, and that may make a difference in my case, but it is worth a try on your machine; just keep dabbing/releasing Esc to see if it works.

---

### Post by syberhunter on 2013-06-25
Thanks! i will check those two things and i have downloaded a copy of the boot repair. I'll have another go at this on the weekend.  S #-o

---

### Post by syberhunter on 2013-06-25
Ok thank you!

---

### Post by buzzingrobot on 2013-06-26
Try the Tab key.

---

