---
title: "Ubuntu 7.10 Gutsy Gibbon x64 doesnt have splsh loading screen"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by asleekaizoku on 2008-01-07
I have had this problems before on Feisty Fawn as well.
I am using a Core 2 Duo processor

Anyone know how to bring it back??

---

### Post by ryanVickers on 2008-01-07
its not a problem, just they decided to have the feature off by default because it was a disaster :p

to turn it on, run ```
gconftool-2 --type boolean --set /apps/gnome-session/options/show_splash_screen 1
``` in the terminal
 and logoff then back on and see if it works :D

---

