---
title: "system hang"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by reverend_HH on 2007-06-07
hello all, i am relatively new to ubuntu but i have done some playing with it so maybe one day i can make the switch from windows. so i installed edgy last night and everything went perfectly, i even started to get some new themes and this is where i encountered my problem. i went to gnome-look.org in search of some themes and when i applied a new mouse theme everything just went wrong. my toolbars and desktop disappeared so i figured if i rebooted everything would be back to normal but it got worse, once i logged in, the brown window that shows the icons loading just stayed brown and the system hangs. it wont respond to any key commands and it just sits there doing nothing. i decided to log in using gnome failsafe and thats how im posting this message. help is greatly appreciated, if any additional info is needed please let me know!

---

### Post by finer recliner on 2007-06-07
when you boot up to grub, choose  recovery mode. this will log you into a terminal with as root. start undoing any changes to your system until the problem goes away.

---

### Post by techuser on 2007-07-27
As a nooby how do you undo change from the terminal? 
I can boot into the root access and from there it is only a terminal with no reference as to which changes were made or what code to access them .
Any advice

---

### Post by AlexenderReez on 2007-07-27
> **techuser said:**
> As a nooby how do you undo change from the terminal? 
I can boot into the root access and from there it is only a terminal with no reference as to which changes were made or what code to access them .
Any advice

i think

> sudo dpkg-reconfigure -phigh xserver-xorg

can help you :)

---

### Post by techuser on 2007-07-27
I tried the:
sudo dpkg-reconfigure -phigh xserver-xorg
The process went well but upon rebooting into Ubuntu the following observations.
1 the Beryl type 4 desktop indicator is now displayed properly where it only showed one desktop previously.
the upper taskbar shows none of the usual auto run programs as loaded
the mouse is movable but does not seem to activate anything.
No keyboard commands are accepted.
Any New ideas?
:(

---

