---
title: "Help Ive Been Having This Problem =("
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by BETOCORELLA on 2007-07-23
Help Me Ive Had This Problem Since Installation. When I Reboot I Get This Black Screen. I Know Its The Screen Resolution Cuz I Messed With That Code Sudo Dpkg-reconfigure Xserver-xorg. It Worked Then I Shutted It Off And Woke Up This Morning With The Same Problem. Please Help...im In Desperate Need

---

### Post by NilsE on 2007-07-23
Try it with this version of the command in a terminal  

sudo dpkg-reconfigure -phigh xserver-xorg

This way you only need to select the video card you have and the resolution your display supports.

My guess is that it still did not like the xorg.conf setup and tried to reconfigure it again.

If this does not work post a little more info like the system and video type.

---

