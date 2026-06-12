---
title: "[SOLVED] screwed up my desktop"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by niki001 on 2007-09-08
Hi all,

Ive been fidling around with compiz - fusion and now i managed to screw up my desktop.
somehow   :lolflag:  i suceeded in removing all my bars from the desktop and now i cant get to any of my progs. Can someone tell me how i can get in to the console and what progs i have to start to get the bars (top bottom left or right) back on screen.

thx

---

### Post by Myglaren on 2007-09-08
Have you tried the Windows stanby of rebooting?
Feisty sometimes loses mine while changing desktops.  A reboot usually fixes it.
I know there must be a fix but Gutsy isn't far away.

---

### Post by overdrank on 2007-09-08
> **niki001 said:**
> Hi all,

Ive been fidling around with compiz - fusion and now i managed to screw up my desktop.
somehow   :lolflag:  i suceeded in removing all my bars from the desktop and now i cant get to any of my progs. Can someone tell me how i can get in to the console and what progs i have to start to get the bars (top bottom left or right) back on screen.

thx

HI you can try to use the command 
```
sudo apt-get install ubuntu-desktop
```
You reach the terminal with the keys alt,ctrl,F1 all at the same time. Hope this helps and good luck!

---

### Post by skymera on 2007-09-08
> **overdrank said:**
> HI you can try to use the command 
```
sudo apt-get install ubuntu-destop
```
You reach the terminal with the keys alt,ctrl,F1 all at the same time. Hope this helps and good luck!


spelling error in above post

make sure you spell 'desktop' not desop :)

---

### Post by overdrank on 2007-09-08
> **skymera said:**
> spelling error in above post

make sure you spell 'desktop' not desop :)

Thanks :oops:

---

### Post by niki001 on 2007-09-08
Thx for the quick responses, people.:)

rebooting doesn't help and instaling ubuntu-desktop neither. I dont think its a problem off missing prog's though. After rebooting amarok starts up (i hear music) but no taskbars appear anywhere ( i had one on top and one on the bottom). But now the're not there anymore. I think by falling back from compiz to metacity i somehow lost the settings.
I'm pretty sure  all i have to do is to manually start up the program for the taskbar, but i dont know what program to use. And i want to do it in graph. mode, so how can i start console up without losing GUI.

thx

---

### Post by alex2035 on 2007-09-08
Alt + F2
then run "xterm" inside the box
:)

---

### Post by niki001 on 2007-09-08
thx Alex,

Already one problem solved (Alt+F2 didn' t work, had to make a starter). Got my console back.
Now what command must i use to start up my taskbars....?? :-k

thx

---

### Post by alex2035 on 2007-09-08
I am at this moment at my Xubuntu laptop, but my PC runs Feisty. There is an access to manipulate all the settings for gnome which I have used frequently. I have lost the bars sometimes and this  thing gets them back (and much more if you need). Its called the configuration editor where you edit the complete gnome database. It is not in the menu by default.  you can pull it with "gconf-editor" , there is a database tree where you find "desktop" and you can fiddle there with everything and probably fix it. Look there for apps/nautilus/desktop or apps/panel/toplevels for some hints.

hope  this helps

---

### Post by niki001 on 2007-09-08
thx for the support,

I found how to solve the problem by logging in via another user.
The app i needed was gnome-panel.

thx all for the hulp
grtz

---

