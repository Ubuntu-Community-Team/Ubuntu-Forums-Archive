---
title: "Can't save text file to /etc/init.d"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by vicrp on 2006-03-27
I am trying to save a wireless configuration text to file to /etc/init.d .  Each time I attempt to save the file in that folder I get an error message:  "Could not save the file /etc/init.d/wifi-start" .

Why can't I save a text file in that location?

---

### Post by Thirsteh on 2006-03-27
Hi vicrp.

You have to be root when you attempt to save the file. Try something like;

Kwrite: sudo kwrite /etc/init.d/wifi-start
Gedit: sudo gedit /etc/init.d/wifi-start
Nano: sudo nano /etc/init.d/wifi-start

And so on and so forth... hope it helps :)

---

### Post by vicrp on 2006-03-27
That did it!  Thanks.

What a great place!

---

### Post by dvarsam on 2006-03-27
Why would somebody want to save a file inside "/etc/init.d"?

Is the file automatically-run during the Ubuntu booting process IF Saved inside that directory?

Thanks.

---

### Post by Thirsteh on 2006-03-27
/etc/init.d is the standard location for initalization scripts used in the different runlevels /etc/rc.0, rc.1, rc.2 etc. (something like that). Basically, all the scripts that are called during startup are in this directory. Nothing happens if you just put a script here, you will need to make a symbolic link to the script from inside one of the rc.x folders. You can toggle startup on a script (make the symlink) located inside /etc/init.d very easily by using either 'bum' or 'rcconf', bum is a GUI (graphical user interface) application where rcconf is CLI (command-line interface).

Simply do either 'sudo apt-get install rcconf' or 'sudo apt-get install bum' to install either of these.

To use rcconf, type: sudo rcconf
To use bum, simply type: bum     (or 'bum &' if you want to be able to close the terminal)

---

