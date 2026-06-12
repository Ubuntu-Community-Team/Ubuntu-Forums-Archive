---
title: "What happened to my Nvidia control applet?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by words1 on 2007-06-01
I just updated to 7.04 from 6.06 (via 6.10), and all is well (mostly), except that I no longer have my Nvidia control center (where you set digital vibrance, etc.).  Card is a GeForce 6600, and driver is whatever the Restricted Driver Manager came up with.  Is there an easy way to get my control center back?

---

### Post by annda on 2007-06-01
you can create a launcher for nvidia-settings (gksudo is needed). is that what is missing?

---

### Post by words1 on 2007-06-01
Excellent -- perfect.  I made a menu item with "gksudo nvidia-settings." Thanks!

---

### Post by Patrick K on 2007-06-01
You don't need gksu. My menu item uses the command "/usr/bin/nvidia-settings". It works fine and no need to enter your password.

---

### Post by forger on 2007-06-01
> **Patrick K said:**
> It works fine and no need to enter your password.
Yes, but that's for viewing pleasure only. gksu shouldn't be used unless you're editing some stuff in /etc/X11/xorg.conf through nvidia-settings (highly **NOT** recommended) :)

---

### Post by words1 on 2007-08-02
How do I get the settings for digital vibrance, etc., to load automatically when I start the computer?  As is, I have to load the control center before they kick in.

---

### Post by words1 on 2007-08-02
never mind -- I found this in another thread:

Run nvidia-settings like this when Gnome starts by putting it in sessions->startup programs
nvidia-settings --load-config-only

---

