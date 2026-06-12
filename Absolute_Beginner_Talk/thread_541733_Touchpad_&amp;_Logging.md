---
title: "Touchpad &amp; Logging"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Lifes Victim on 2007-09-03
I'm trying to disable my touchpad on my laptop, I have installed gsynaptics (Touchpad), and now I need to edit xorg.conf and add some things, but it is set as read only. How do I edit it?

Secondly, when I logout the screen goes black and stays that way causing me to have to cold reboot. How do I stop this?

---

### Post by ggaaron on 2007-09-03
You need to be root to edit this file, do sudo (your editor here) /etc/X11/xorg.conf, or for kde kdesu (your editor here) /etc/X11/xorg.conf, and for gnome I'm not sure if it is the right program name gtksu (your editor here) /etc/X11/xorg.conf.

---

