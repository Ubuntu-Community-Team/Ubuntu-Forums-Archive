---
title: "i cant turn off my computer any more!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by krazed nun on 2006-09-01
when i click 'quit' the only options are
log out, lock screen, switch users, and hibernate. i am really scared/confused right now.:o

---

### Post by nudnik on 2006-09-01
Although I am sure there is another more elegant way to solve this problem, you can shut down the PC using the following crude method:

Press Ctrl-Alt-F1
This will bring up the command line interface. Press the power button once, assuming you are running an ATX or BTX system, and Ubuntu should begin shutting down the OS as it would if you had selected the "power down" option using the GUI.

You can then breathe deeply and drink some warm milk and honey to calm down:D

---

### Post by jordanmthomas on 2006-09-01
Have you done something silly like start a second X Session?  If so, only the display on :0 will be able to turn off the computer.

Until you figure it out, you can just log out and Shut Down from there (probably)

---

### Post by TrIde2188 on 2006-09-01
surely u can just hold down the power button? ;)

---

### Post by toasted on 2006-09-01
You could open a terminal and do:
```
sudo reboot
```

Or just log out then choose shutdown

I have XGL/complize installed and I get that too. First I log out, then I reboot.

---

### Post by Fully216 on 2006-09-01
You can also shutdown from the command line as well.  the command shutdown (so appropriately named) does the trick.  Just type man shutdown for options or go here:

[http://www.ss64.com/bash/shutdown.html](http://www.ss64.com/bash/shutdown.html)

This should be no different as if you had used the gui.  The reboot command works too, but only if you want to restart your computer not turn it off.

---

### Post by toasted on 2006-09-01
Reboot and see if its the same next boot... if it is post back

---

### Post by xhaan on 2006-09-01
I get this problem, but only when I start Gnome using startx. When I login from GDM the shutdown button comes back.

---

### Post by krazed nun on 2006-09-01
many of these methods of turning off my computer work, but is there any way that i can get the shutdown icon back? i am just so lazy. startx looks good but i am sort of confused about what it really is. thanx in advance!:wink: :D

---

### Post by xhaan on 2006-09-02
startx is just a small script that starts the x window system if youre in console. In other words it's just another way to start Gnome without using GDM (or KDE without using KDM, etc) 

It probably won't fix your problem, sorry if I confused you... wish I could help, I'd like to know the answer to this problem too.

---

### Post by 3rdalbum on 2006-09-02
Can't you just do "log out", then when the login screen comes up, go to the Options menu and choose "Shut Down"?

Or put a launcher to "gksudo halt" in one of your gnome panels?

---

### Post by krazed nun on 2006-09-02
I made a shorcut to shut my comp down. I went to alacarta menu editor and added a new launcher. For the command, i wrote 'sudo shutdown -h now'. Then, i made shortcut to it in the top panel. When i press it, i goes to a login screen but after a few seconds it goes to usplash screen, showing that it is shutting down. I didnt get the icon back, but atleast i found a way to shut it down. Thanks guys. :D

---

