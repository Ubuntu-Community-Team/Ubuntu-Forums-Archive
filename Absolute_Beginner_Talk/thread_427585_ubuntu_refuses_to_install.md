---
title: "ubuntu refuses to install"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by StarFire039 on 2007-04-29
Reinstalling ubuntu, and it just won't have it! When I install it, I select install ubuntu as usual and the bar animates, and after it's done the screen just goes blank, yet I can still hear the welcome chime. This CD is the same one I used to install on this same PC and it worked fine, but now it won't have it. Won't install in safe mode either. Tried the alternate CD, won't work either (hangs on "select software to install"), tried Xubuntu and that has the same problem. Any ideas? Thanks in advance.

---

### Post by StarFire039 on 2007-04-29
bump

---

### Post by madmetal on 2007-04-29
well can you tell us more about your system?
vga card? ram ? cpu?
have you checked the cds if they got problems?

---

### Post by Loki-uk on 2007-04-29
when you get the black screen press CTRL + ALT + F1 and then at the prompt type sudo dpkg-reconfigure xserver-xorg and just answer the question until you get to the end. Then reboot

Your graphics card isn't configured properly.

Loki

---

