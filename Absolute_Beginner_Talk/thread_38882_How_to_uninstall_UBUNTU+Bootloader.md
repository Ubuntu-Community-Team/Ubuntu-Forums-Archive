---
title: "How to uninstall UBUNTU+Bootloader"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by imperator1967 on 2005-06-02
How can I uninstall ubuntu including GRUB Bootloader? I am thinking about installing another distribution instead.

Any ideas?

---

### Post by Roshan on 2005-06-02
[QUOTE=imperator1967]How can I uninstall ubuntu including GRUB Bootloader? I am thinking about installing another distribution instead.

Any ideas?[/QUOTE]
 Well, you could install the other distribution into the same partition that you created for Ubuntu, and ensure that that distro's bootloader is installed into the same location that Ubuntu's GRUB is installed in.  Other than that, you don't actually uninstall a boot loader - you overwrite it with the boot loader of another operating system (which for example Windows is very fond of doing without even asking you, every time you install Windows)

---

### Post by tikal26 on 2005-06-02
[QUOTE=imperator1967]How can I uninstall ubuntu including GRUB Bootloader? I am thinking about installing another distribution instead.

Any ideas?[/QUOTE]
 You probably don't need too the other distribution would ask you to waht partition you wan to intall to and they would erase wahtever is on your partition and install the new dist.
good luck

---

### Post by kvidell on 2005-06-02
[QUOTE=tikal26]You probably don't need too the other distribution would ask you to waht partition you wan to intall to and they would erase wahtever is on your partition and install the new dist.
good luck[/QUOTE]
 What he said.
But! If you're really worried (Why would you be?), pop in the Ubuntu install CD and make like you're going to install the OS.
The first time you get asked a question, hit the "back" choice, then scroll to the bottom of the list and choose "Execute a Command Prompt" and say "Okay" (or is it yes?) to the warning/question thinger.

mke2fs /dev/hd?
If you don't specify a partition label (Note that I leave a questoin mark in place of a DRIVE label, not a partition label. Please give it the alpha-label for your drive) it'll whine that you didn't, pat it on the back and tell it to keep walking and in a few moments ~everything~ will be obliterated from the drive.

Hope that helps,
- Kev

---

