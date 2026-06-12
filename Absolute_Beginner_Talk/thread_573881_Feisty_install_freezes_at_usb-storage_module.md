---
title: "Feisty install freezes at usb-storage module"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by dr.flodo on 2007-10-12
A number of users have reported that Feisty installations freeze with a message "loading module usb-storage" at 90% complete. I haven't found any resolutions, but these comments from a variety of forums may be helpful if you are having this problem, which is hassling me right now.:confused:

1. The installation may not be frozen, just slow, like really slow. The hard drive shows continuous pulses of activity every second. Hitting Ctrl-Alt-Backspace will stop the installation and display the desktop as far as it got, although there won't be any functioning USB ports, and the grub boot loader won't completely install.

2. Some users have reported failure to load Windows after this problem, although this didn't happen with me. If this does happen, try switching drives, and rebooting, and if necessary, you may have to recover Windows using emergency disks or the XP recovery console.

3. Several people reported that the problem can be resolved by disabling USB from the the BIOS. Also, it might help to unplug USB hardware during the install. This would be a drag to install USB later, since my internet connection is through USB.

4. One person said to stick with Ubuntu version 6.10 until they have it sorted out.

5. One person said they solved the problem by installing from the Alternate CD.

I sure would be interested in knowing how pervasive this problem is.

---

### Post by dr.flodo on 2007-10-12
Oh yes, the system (my reply to me).

Computer specs:
  Asus M2NBP-VM CSM motherboard
  AMD 64 4800+ CPU
  2GB RAM
  NVIDIA nForce Network Adapter (unplugged)
  Onboard Display adapter: NVIDIA Quadro NVS 2105/NVIDIA GeForce 6150LE
  HDD 0 Seagate IDE 160 GB backup drive FAT32
  HDD 1 Seagate IDE 20 GB ext3 (intended Ubuntu install drive)
  Extra SATA Drive with Win XP 250 GB multiple partitions, FAT32

---

