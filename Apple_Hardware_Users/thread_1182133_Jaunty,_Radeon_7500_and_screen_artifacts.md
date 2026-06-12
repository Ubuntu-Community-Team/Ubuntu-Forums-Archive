---
title: "Jaunty, Radeon 7500 and screen artifacts"
date: 2009-06-08
forum: Apple Hardware Users
---

### Post by igor_av on 2009-06-08
Hi. I recently installed Jaunty on a G3 iBook (900 mhz, Radeon 7500). As expected, 3D acceleration was non-working with the bundled kernel. I installed the one from 8.10, and also built the newest version (2.6.29-4) from source... In both cases, I got working 3D acceleration, but I now have screen artifacts on some GUI elements (highlighted menu items, progress bar). The weird thing is that if I change the Gnome theme, different elements will be affected (ie, menu items become ok, but text input fields become garbled).

If the visual effects are turned off, everything go back to normal.

The problem appears both in Ubuntu and Xubuntu.

Any idea?

Thanks.

---

### Post by davidmigl on 2009-06-23
I have the same problem, but I don't have a solution. I have a desktop radeon 7500 PCI card. Yes, it is very old, but it is sufficient for my (and probably 80%+ of other people's) uses of basic internet + text editing + spreadsheets.

This does seem to be a known issue with compiz: [https://wiki.ubuntu.com/CompizTeam](https://wiki.ubuntu.com/CompizTeam).

---

### Post by igor_av on 2009-06-24
> **davidmigl said:**
> I have the same problem, but I don't have a solution. I have a desktop radeon 7500 PCI card. Yes, it is very old, but it is sufficient for my (and probably 80%+ of other people's) uses of basic internet + text editing + spreadsheets.

This does seem to be a known issue with compiz: [https://wiki.ubuntu.com/CompizTeam](https://wiki.ubuntu.com/CompizTeam).

Hi. This is not only an issue with Compiz : 3D acceleration in broken.

Finally, I installed Debian instead. It is less polished, but much more reactive (and customisable).

---

