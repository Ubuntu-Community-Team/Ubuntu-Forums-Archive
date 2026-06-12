---
title: "Does GRUB overwrite on Reinstall?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-01-07
Hi.

I want to re-install Ubuntu, and this will be the third time.  I just want to make sure that when GRUB is installed on hd0, the files overwrite the old ones, rather than just install another copy. Can someone confirm that GRUB does in fact overwrite the files, or should I use Windows Recovery console to fix the MBR before re-installing Ubuntu again?

---

### Post by ajmorris on 2007-01-07
GRUB should overite the old grub on install because it is installed to /boot/grub and it will ovewrite old files of the same name. Any files that are in that folder that don't have the same name as a file that grub installs will not be overwritten however.

---

