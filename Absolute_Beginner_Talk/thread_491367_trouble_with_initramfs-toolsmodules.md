---
title: "trouble with initramfs-tools/modules"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Pde on 2007-07-03
After a lot of trouble installing Feisty (getting it to boot)  I found a workaround that involves adding "piix" to initramfs-tools/modules and running "sudo update-initramfs -u".  I am fairly new to Linux and I can't figure out how to do this, as the modules file is read-only and I can't change the permissions.  How do I add something to the modules file?

---

### Post by jpeddicord on 2007-07-03
Instead of just opening the file directly, open a terminal and type this:
```
gksu gedit /file/to/edit/initramfs-tools/modules
```(Of course, change the filename :))

You will be asked for your password, and after you enter it you should be able to edit the file until you close Gedit.

Jacob

---

