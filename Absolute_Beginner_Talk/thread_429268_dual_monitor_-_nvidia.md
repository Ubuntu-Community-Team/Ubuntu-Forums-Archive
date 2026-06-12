---
title: "dual monitor - nvidia"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by sharondaniel on 2007-05-01
I have install feisty with dual monitor, had few problems getting the order right, i.e. the left screen appeared on the right, so in the end i have switched the physical connector on the back of the PC and it is working fine. However, since than, when I restart Ubuntu the second screen doesnt show anything, it says no signal, but when I restart X (Ctrl + Alt + BSpc) it works. 
Does anyone know why it doesnt start on reboot but it does after X restart?

---

### Post by jiminycricket on 2007-05-01
Have you tried to configure using the 'gksudo nvidia-settings' GUI?  That has pretty fine-grained controls for detecting dual monitors.  You just  need to save the X file it generates to /etc/X11/xorg.conf for it to work after you reboot (there's an option for that right in the dual monitor configuration screen).

---

### Post by sharondaniel on 2007-05-01
great, i didn't know about this command, but when I used it, it helped me a lot.

---

