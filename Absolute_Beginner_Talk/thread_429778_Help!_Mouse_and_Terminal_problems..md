---
title: "Help! Mouse and Terminal problems."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by OscarL on 2007-05-01
My mouse stopped working, I can't click on anything! Unless I hold down the ctrl button. Also the Terminal just opens like a white box, can't type anything into it.

---

### Post by Seisen on 2007-05-01
have you done any updates lately or messed with your xorg.conf file?

---

### Post by starcraft.man on 2007-05-01
The white box hints that you may have just installed 3d graphics drivers? Yes? If so, easy fix I think. Reboot your computer and at the grub menu, boot in recovery mode. Then, when your in go to terminal and type in:

```
sudo dpkg-reconfigure xserver-xorg
```

In that auto config of your xorg file, make sure to select nv, as your graphics driver. Your install must have been bad, or the xorg.conf file messed up when you installed automatically. Take out whatever install you did, and use Envy, great isntaller :)

Hope thats the terminal problem, might be mouse too.

---

### Post by OscarL on 2007-05-01
Thanx guys! Found out that the Desktop EFfects was enabled and they messed everything up for me!

---

