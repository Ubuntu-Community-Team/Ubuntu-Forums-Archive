---
title: "grub!"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-04
i want to know that once i installed grub(which is now disfunctional in my case) can i reset my computer to boot from the original boot.ini or whatever the windows boot is called?

---

### Post by amohanty on 2006-11-04
If you have windows installed and you install grub using the install cd or grub-install, it will automagically detect the windows boot loader and prompt you to add it to the list of bootable partitions. Say yes and you will see windows in the list of available operating systems.

In any event to get back the NT loader, you just need to boot from the XP setup cd and hit repair when prompted.

Also if your grub is dysfunctional, search for grub restore mbr in the forums, its been asked and answerd about a gadzillion times :)

HTH
AM

---

