---
title: "Help Linux Noob"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by blustori on 2005-07-15
Hi, I initially had dual boot windowsxp / ubuntu, but I got mad at windows and deleted it by formatting my ntfs drive. I should have resized my fat32 drive to take up the space after formatting, but I forgot. Is there a way to resize my fat32? Also, is there any way to disable the choose OS option and boot straight into ubuntu? Basically I want to get rid of the dual boot option. Thanks in advance.

---

### Post by aysiu on 2005-07-15
[QUOTE=blustori]Hi, I initially had dual boot windowsxp / ubuntu, but I got mad at windows and deleted it by formatting my ntfs drive. I should have resized my fat32 drive to take up the space after formatting, but I forgot. Is there a way to resize my fat32? Also, is there any way to disable the choose OS option and boot straight into ubuntu? Basically I want to get rid of the dual boot option. Thanks in advance.[/QUOTE] While there are ways to get rid of the dual boot option and resize your existing FAT32 partition, if you know for certain you want just Ubuntu, the cleanest and easiest way to do this may just be to back up your /home directory and to a clean reinstall of Ubuntu.

---

### Post by blustori on 2005-07-15
I resized my partition using gparted and now all I want to do is get rid of the dual boot option when I start my computer. Any ideas? I boot in using grub.

---

### Post by aysiu on 2005-07-15
[QUOTE=blustori]I resized my partition using gparted and now all I want to do is get rid of the dual boot option when I start my computer. Any ideas? I boot in using grub.[/QUOTE] Have you tried editing /boot/grub/menu.lst and changing timeout to 0?

---

