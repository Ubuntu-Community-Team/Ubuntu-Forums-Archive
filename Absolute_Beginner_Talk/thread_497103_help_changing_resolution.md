---
title: "help changing resolution"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2007-07-09
I just bought a new 24" monitor that says the recommended resolution is 1920 x 1200. Does anyone know how I can make it so I can change the screen resolution currently my max resolution is 1680 by 1050. Thanks

---

### Post by Happy_Man on 2007-07-09
Try the command ```
sudo dpkg-reconfigure xserver-xorg
``` Keep hitting enter until you get to a long list of resolutions, choose all that you want with spacebar, keep hitting enter until it finishes. Now, press ctrl-alt-backspace, and log in again. You should be able to change your resolution to 1920x1200.

---

### Post by cptjaben on 2007-07-09
Thanks for the help.

---

