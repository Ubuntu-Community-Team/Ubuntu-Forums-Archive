---
title: "Radion / Resolution probs.."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by VexD on 2006-07-28
Ok, my friend just switched to Ubuntu and he has a ATI Radion 200 and his res is stuck on 640x480 and w.e, any idea why? :eek:

---

### Post by rck_hitokiri on 2006-07-28
had the same problems before.... type this command ond the console.
or terminal.

sudo dpkg-reconfigure xserver-xorg.
you can accept all the comming questions until you get to your monitor settings then change 16 bit to 24 bit. meium to high. and modify your resolution. reboot after doing so.

---

