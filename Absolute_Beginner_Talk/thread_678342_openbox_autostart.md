---
title: "openbox autostart"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-01-25
okay i have an openbox auto start and what not the only problem is gtk will not start with my selected gtk theme. if someone could i am trying to get pypanel and tint to start at startup with my selected gtk theme. Can anyone help me?

---

### Post by urukrama on 2008-01-25
For pypanel and tint, add the following lines to your autostart file:

> pypanel &
ttm &

For you gtk themes, you have several options. You could use the gnome settings (gnome-settings-daemon) or xfce settings (xfce-mcs-settings) and add those to the autostart file, or you could specify the Gtk theme, fonts and icons in the .gtkrc2.0 and gtkrc.mine files. See my Openbox guide for more details (link in signature).

---

