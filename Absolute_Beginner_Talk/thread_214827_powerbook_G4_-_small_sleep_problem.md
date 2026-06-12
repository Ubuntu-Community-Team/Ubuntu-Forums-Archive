---
title: "powerbook G4 - small sleep problem"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by silversurfer2025 on 2006-07-13
Helo world,
I installed ubuntu 6.06 on my powerbook g4 last night and I am impressed how well everything worked out so far (esp. compared to yellow-dog-linux which I had tried out before).

Nevertheless, I have some minor problems with my system:

1. sleep works perfectly well, if I manually let the system sleep (either through "pbbcmd sleep" or in the "shut-doen, restart, hybernate, etc" area. However, the system does not go to sleep when I close my laptop/the lid. Is there any small configuration which I would have to set in order to get this to work? I trief kubuntu from liveCD and it worked perfectly well there...

Thanks for your help
Tim

---

### Post by silversurfer2025 on 2006-07-14
I figured it out myself.. If you kill the gnome-powermanager process in system monitor everything works fine. Seems as if the gnome and pbbuttons do not work together..

Is there a way how I can prevent the gnome powermanager from starting on reboot?

---

### Post by silversurfer2025 on 2006-07-14
AAAH I AM SO STUPID!!!

I just found out that the "what-to-do-on-closed-lid" preference of the gnome-power-manager was not set to suspend...

Argh... Sorry for the trouble, it is all fine now.

Greetings
Tim

---

