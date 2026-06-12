---
title: "Can see all of install app"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by AnalogKid on 2006-07-09
Ok, downloaded Ubuntu, played with the liveCD some, so I decided to install the program.  My screen res is at 640x480 because the Screen Resolution program doesn't offer any other options.  My graphics card is a built in gForce2 card.  I tried to install the NVIDIA drivers, but the help file in Drapper says you have to have an install (NOT LiveCD) to install them.  I can't install because the install program is hidden because it's at a higher resolution than 640x480 and doesn't contain scroll bars(which is kinda dumb if you ask me).

Any suggestions?

---

### Post by taurus on 2006-07-09
Why don't you install Dapper using the alternate CD.  You can install it directly from the CD, no need to boot into live first.  Then, install nVidia driver for it and configure it to whatever resolution you want to use in /etc/X11/xorg.conf.  ;)

---

### Post by AnalogKid on 2006-07-10
Ok, I tried this... I now have a command line version of Ubuntu installed.  Which is mostly not useful to me.  I understand I need to start Xwindows or something, but I have no idea how to do this.  Any suggestions?

---

### Post by nalmeth on 2006-07-10
Did you do a server install? If so, it won't leave you with a desktop environment.

at the command prompt, type:
sudo aptitude install ubuntu-desktop

for whatever reason, it's possible the GUI was just not installed.
If it was, and X is causing the problem, try

sudo dpkg-reconfigure xserver-xorg

---

