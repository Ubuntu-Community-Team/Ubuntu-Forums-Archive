---
title: "[SOLVED] Terminal Command Line"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Officer Dibble on 2007-10-24
Hi,

I just need a terminal command line to set my resolution and refresh rate to defaults, please.

Any very basic default resolution and refresh rate will do, I just want to be able to see my desktop again. Ubuntu keeps changing it now and again and I just want a quick fix.

At the moment all I have access to is CTRL-ALT-F1 (and then CTRL-ALT-F7 to get out of it again) to allow me to boot into Ubuntu.

Please help, this is driving me mad and I have things to do.

---

### Post by realvz on 2007-10-24
sudo dpkg-reconfigure xserver-xorg -phigh

---

### Post by Officer Dibble on 2007-10-24
> **realvz said:**
> sudo dpkg-reconfigure xserver-xorg -phigh

Thank you very much, this was perfect. :guitar:

---

