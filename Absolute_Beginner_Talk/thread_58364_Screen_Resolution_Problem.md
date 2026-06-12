---
title: "Screen Resolution Problem"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by Rick069 on 2005-08-19
I've just installed Ubuntu and I have a problem. Everything is @ a 640x480 screen resolution, but I have a 17" flat screen monitor. I figured I can go to the screen res option and change it to 1280x1024 with a refresh rate of 75, but there is no other option other than the 640x480 option with a 60 refresh rate. I would like to know step by step how I can modify whatever to change to the desired screen res of 1280x1024 with the refresh rate of 75?

---

### Post by aysiu on 2005-08-19
I guarantee that if you read one of [these threads](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+screen+resolution+vertrefresh+horizsync&btnG=Google+Search), you'll find the solution. Let us know if you still can't do it and what you've tried.

---

### Post by Rick069 on 2005-08-19
Ok cool. I've made up my own file for the screen res and since I've only worked with this particular distro, how do I access:/etc/X11/XF86Config-4 and modify this file to show the new changes I've made?

---

### Post by aysiu on 2005-08-19
[QUOTE=Rick069]Ok cool. I've made up my own file for the screen res and since I've only worked with this particular distro, how do I access:/etc/X11/XF86Config-4 and modify this file to show the new changes I've made?[/QUOTE] Are you sure you're using XFree? You probably have /etc/X11/xorg.conf instead (if you're using an up-to-date version of Ubuntu). 

Open up a terminal.
Type *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup*
Then, type *sudo gedit /etc/X11/xorg.conf*

Edit. Then, restart the X server (Control-Alt-Backspace) or reboot to see the changes.

---

### Post by Rick069 on 2005-08-19
Everything is fine now. Thx a lot. I have something else that has gone wromg or shall I say is a case of me not knowing how to do it. It'll be under another post.

---

