---
title: "Unable to start the settings manager 'gnome-settings-daemon"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by giorgiomartini on 2007-10-25
this is what i get after solving the nvidia-glx problem.



Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.



how do i fix the gnome thing ? im a total noobie.

---

### Post by bu.sahl on 2007-10-25
I'm getting the same message when I try running gnome-appearance-properties from the command line (using sudo) .
when I try running it via (system > preferences > appearance) It just doesn't work and causes high process load .

I'm using gutsy and the problem started when I installed kde packages .

---

### Post by SleepWalkerX on 2007-10-26
Getting the same problem.  I can change the theme back if i reinstall gtk-theme-switch and use that, but the icons stay the same.

---

### Post by quantboy on 2007-11-26
Getting the same problem- anyone know how to fix this???:confused:

---

### Post by rahimveron on 2007-11-26
Try using terminal and use ```
gnome-settings-daemon
``` and you might get your themes, icons, etc working. Another thing i did to solve this problem last night was restarted X by Ctrl+Alt+Bacspace and rebooted. 
This solved my problem. Gees this problem is getting reported in other threads too.

---

### Post by ztomic on 2007-11-29
edit* removed by poster

---

