---
title: "Just Installed, dual-boot, and I NEED 1280x800.  I edit xorg.conf, but how?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-04-06
I know I have to access via terminal, is it sudo edit xorg?  I have looked for a few guides but none have worked, I have an emachines laptop 15.4 screen, nvidia geforce 6100 video card.

i would not be so titchy but I just am not able to work in any resolution lower then that.

If possible, could I also use dual monitors?  with 1600x1200?

---

### Post by gborzi on 2007-04-06
If you are in graphical mode (gnome, kde or whatever) use > sudo gedit /etc/X11/xorg.conf, otherwise use > sudo nano /etc/X11/xorg.conf. gedit is a graphical editor which is installed by default, nano is a terminal editor, that should also be installed by default.

---

