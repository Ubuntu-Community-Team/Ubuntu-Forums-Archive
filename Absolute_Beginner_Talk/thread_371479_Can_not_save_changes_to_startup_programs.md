---
title: "Can not save changes to startup programs"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by dixon151 on 2007-02-27
Hey new at linux of course. This sounds really really stupid but its really annoying also so i thought i would ask somebody smarter than myself. anyways i am using 6.10 edgy on dell 700m. and i am trying to set up certain programs to start up as soon as i log in ie beryl-manager or conky etc....,i open up session under preferences and navigate to session and add the program i want. but it does not save anything i do for some reason. in terminal i get this

** (gnome-session-properties:16707): WARNING **: Could not save /usr/share/gnome/autostart/gnome-power-manager.desktop file

---

### Post by tronica on 2007-02-27
did you disable gnome power manager? also try running this from the terminal and see if it works.

> sudo gnome-session-properties

---

### Post by dixon151 on 2007-02-27
wow awesomely simple to fix thanx man.

---

