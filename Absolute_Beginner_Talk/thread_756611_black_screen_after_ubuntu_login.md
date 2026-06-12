---
title: "black screen after ubuntu login"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by dark_j3di2 on 2008-04-16
I changed the resolution on ubuntu to blank or something similiar and when i login i cant see the desktop. its just a black screen. is this a common problem?

---

### Post by talsemgeest on 2008-04-16
Yeah, it means that you have selected a resolution that either your graphics card or monitor can't display. If you can't get to your desktop, boot into recovery mode and type ```
dpkg-reconfigure xserver-xorg
``` and follow the steps.

Hope this helps :)

---

