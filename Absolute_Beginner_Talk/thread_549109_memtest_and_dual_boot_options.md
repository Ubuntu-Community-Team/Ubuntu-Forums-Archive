---
title: "memtest and dual boot options"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by HawkST on 2007-09-12
Hey - what is memtest and why does it start again when 'pass' gets to 100%? Also, how can I fix any errors it finds?

Also, how do I configure the dual boot options so instead of having loads of options (at the moment I have Ubuntu 2.15, Ubuntu 2.15 recovery mode, Ubuntu 2.16, Ubuntu 2.16 recovery mode, Ubuntu memtest (default? why?) and XP) I have just one version of Ubuntu, one recovery mode, memtest and XP as default (for my mum when she uses it)

---

### Post by mcduck on 2007-09-12
1. Memtest is a stress test to confirm that your RAM is working correctly. To get reliable results you should not run it just once, but for long time instead. I recommend at least overnight, as memory errors often start appearing only after continuous stress. If you get even a single error your RAM is broken and you should replace it as soon as possible to make sure your computer works correctly and your files are safe.

I've found that any computer hardware store where people actually know anything about computers accepts memtest errors as proof of faulty RAM, so if the computer/RAM stick is new you should be able to replace it with no cost.

2. Open the grub configuration file for editing ('gksudo gedit /boot/grub/menu.lst'), find the line "# howmany=all" under default options, and change the 'all' to number of kernels you wish to have entries in Grub (Do NOT remove the '#' from the beginning of the line, all default options are supposed to have it!).

Anyway, after kernel update when you have booted with the new kernel and confirmed that everything works correctly you can safely uninstall the old kernel versions with Synaptic. This will also remove their entries from Grub.

To change the default boot option find the line with 'default		saved' (or whatever number), and change the number to the boot option you wish to be default, starting from 0. Or set it to 'saved' like I have, and the default will always be the last used option.

---

