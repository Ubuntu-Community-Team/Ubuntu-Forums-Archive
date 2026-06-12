---
title: "Help, dont know what do do...??? Please"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by samanosuke1983 on 2007-10-06
Hi Friends...

I am running Ubuntu on my laptop.

Toshiba Satellite L35
Celerom M 1.4Ghz
512 mb RAM
ATI Radeon Xpress 200M 256mb
Ubuntu Feisty Fawn

This is the thing.

I used to have compiz and emerald running, it was running smoothly with no problems, also had Avant Window Navigator and Cairo Clock.

Yesterday when i turned on the lap, it took so long to start, my xgl session was very sloooooow, i couldnt work with that performance. So i login into the simple Gnome Session, and i had no problems.

I disable compiz from loading at startup in my xgl session, and it runs normal again, but when i enable compiz (compiz --replace) it shrinks down, and it becomes very slow and unstable...

I dont know what to do, i was running XGL + Compiz + Emerald smoothly two days ago, i did some research, and i disable the restricted controllers for ATI, restart, enable them again, and restart again, and i login to my XGL session and i had all the screen distorted, and i couldnt see a damn thing.

I don't know what to do, im using the simple gnome session, i miss Compiz...

:(

Any help will be appreciated...

:)

---

### Post by rickycodie on 2007-10-06
you might try this

In a terminal type
Code:

sudo gedit /etc/X11/xorg.conf

scroll down to the Devices section and add the following:
Code:

Option "AddARGBGLXVisuals" "true"

Save the changes and restart your computer (or just press Ctrl+Alt+Backspace). The 'bars' should appear now.
__________________

---

### Post by gn2 on 2007-10-06
Install Beryl instead?

---

