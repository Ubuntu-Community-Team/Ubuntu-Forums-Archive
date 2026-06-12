---
title: "Synaptics Touchpad"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by nic2 on 2005-07-18
The touchpad on my HP notebook is behaving strangely (eg. left click = middle click in web browser etc.)  After some reading on the Wiki I understand that I have to change the synaptics touchpad driver parameters, but with my limited knowledge of Linux and the command line I am uncertain as to how to go about it.  Can someone please assist in giving me some guidelines in this regard, thank you.

---

### Post by damonw5 on 2005-07-18
[QUOTE=nic2]The touchpad on my HP notebook is behaving strangely (eg. left click = middle click in web browser etc.)  After some reading on the Wiki I understand that I have to change the synaptics touchpad driver parameters, but with my limited knowledge of Linux and the command line I am uncertain as to how to go about it.  Can someone please assist in giving me some guidelines in this regard, thank you.[/QUOTE]
 To edit the parameters, you need to open a terminal. You can do this by going to Applications->System Tools. Once you are there, enter the following:

sudo gedit /etc/X11/xorg.conf

(case matters! that first X is uppercase, second is lowercase)

Then you can edit the "mouse" section of this file. When you are done, save it, close it, and hit ALT+CTRL+BACKSPACE to restart the "X server" (graphical interface).

What model notebook do you have? Knowing this will help me help you further.

---

