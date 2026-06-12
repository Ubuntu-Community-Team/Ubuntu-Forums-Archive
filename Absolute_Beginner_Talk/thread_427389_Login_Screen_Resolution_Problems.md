---
title: "Login Screen Resolution Problems"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by SuperCow56 on 2007-04-29
Right after my computer finishes booting, or I log out, the Login Screen's resolution is WAY to high. Though after I login it changes back to normal size. Help? im using Gnome and a nVidia GeForce 5200 128mb.

---

### Post by mrpaco on 2007-04-30
The best thing I can think of at this time is to edit /etc/X11/xorg.conf and remove the resolutions that are too high.  You can also run: ```
sudo dpkg-reconfigure xserver-xorg
``` to configure xorg.conf using a wizard.  Be sure to back the original up before you make any changes.

---

