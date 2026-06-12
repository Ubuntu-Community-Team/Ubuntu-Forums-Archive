---
title: "Resolution Problems/Drivers?"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by g0sp3L on 2006-03-01
At 1024x786, the screen does this thing where the top toolbar is at the bottom, and when I move my cursor to the very top of the screen, it appears at the bottom of the screen. Kind of hard to explain. When I set my resolution to 800x600, it fixes it, but most windows I am trying to view are "too big" and I can't see the bottom of the window (where most of the "cancel" and "ok" buttons are.) This makes it painfully hard to do anything, and I end up having to use the tab button and blindly hit enter to see what option I've chosen, which scares me to do. Do I need drivers for my monitor (which is an HP flat screen I ganked from my girlfriend's box)?

---

### Post by Brunellus on 2006-03-01
yeow.  Do the following and see if this doesn't help:

1) hit CTRL + ALT + F1

you sould see a black textmode login.

2) log in 

3) execute

sudo dpkg-reconfigure xserver-xorg

4) follow the prompts.  When you come to the "resolutions" that you want, be sure that the native resolution for your screen is among the choices.  

5) when it's all over, your /etc/X11/xorg.conf file will have been rewritten.  hit CTRL + ALT + F7 to get back to X, and then give it a three-fingered salute of CTRL+ALT+BACKSPACE.  That'll restart the Xserver.

Log back in and see if that didn't help any.

---

