---
title: "Openbox question"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-27
How can i get pypanel and some other programs to start default on openbox. I can seem to find like a startup file at all

---

### Post by fedex1993 on 2007-12-27
does anyone know how to make pypanel startup on star with openbox PLease help

---

### Post by urukrama on 2007-12-27
Add this to your autostart file (an example is in /etc/xdg/openbox/autostart.sh; copy that to /home/USERNAME/.config/openbox/autostart.sh if you don't have one already):

> pypanel &

The link in my signature contains more info.

---

