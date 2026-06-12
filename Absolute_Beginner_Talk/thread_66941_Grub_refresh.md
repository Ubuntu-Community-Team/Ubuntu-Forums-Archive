---
title: "Grub refresh?"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by rj686 on 2005-09-18
I wanna install mepis on another partition on my hdd but im not going to override my ubuntu grub thats already in the mbr. Is there a way to refresh grub.conf without manually editing it?

---

### Post by aysiu on 2005-09-19
You could [reinstall Grub](http://ubuntuforums.org/showthread.php?t=24113) using the Ubuntu live CD, but honestly it's a lot easier to just manually edit the Grub menu.lst.

Just, as root, open Ubuntu's /boot/grub/menu.lst and, as root, open Mepis' /boot/grub/menu.lst and copy and paste the Mepis entry into the Ubuntu menu.lst.

That's it.

---

