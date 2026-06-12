---
title: "HZ and ? after Startup"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by vinodis on 2006-05-10
Hi , i was fascinated by ubuntu talk and tried installing it on my AMD64 machine.
The installation went on well but after the final restart the gui will not start.
All i get is a text box with green border saying "HZ..?" circling all around my screen. I assume my monitors refresh rate might not be set properly.
Is there a way to resolve this issue quickly? or is there a commandline utility to configure X Windows. Pls help and thanks in advance.

---

### Post by dickohead on 2006-05-10
You can drop into the command line:

Control +Alt + F6
or F1, F2, F3, F4, or F5

and then login and edit the file:

sudo vi /etc/X11/xorg.conf

and then specify either of the following:

The driver for your graphics card, which may be set to something like - nv/nvidia/ati, change it to vesa (safer).

Change your maximum resolution value from say... 1600x1400 to 1024x768, or whatever you want, if it's already set to something lower then try the above, or you can locate your monitors manual and input the Horiz and VSync  values (or similar) to work for your monitor.

Good luck!

---

### Post by louis_nichols on 2006-05-10
It is indeed a refresh rate issue.

When it appears, press Ctrl+Alt+F1 and login there, in a terminal session. Then stop the graphical environment with

```
sudo /etc/init.d/gdm stop
``` Aftre this use the command

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the steps there. Then restart the GUI with the command

```
sudo /etc/init.d/gdm start
```

EDIT: forgot something

---

### Post by vinodis on 2006-05-10
Thank you very much. I will try this and report back.

---

