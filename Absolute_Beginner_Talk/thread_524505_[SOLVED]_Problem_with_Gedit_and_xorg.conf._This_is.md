---
title: "[SOLVED] Problem with Gedit and xorg.conf. This is weird"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-13
Ok, this is weird. After doing a reconfigure and everthing runs fine. I tried to use the command 
sudo gedit /etc/X11/xorg.conf it loads the file but its completely blank.

Now if I file browse the file and open it it's all there.

If I use 

sudo nano /etc/X11/xorg.conf it shows up ok.

So gedit must be cocked up somehow, any ideas. :confused:

---

### Post by 1/0 on 2007-08-13
Try it with gksudo instead.

---

### Post by philinux on 2007-08-13
Same thing I'm afraid. Nano works vim comes up blank as well

---

### Post by fastpakr on 2007-08-13
Are you using Tab to get it to pre-type the file name or manually typing it?  Somehow you're screwing up the path and it's creating a blank file.

---

### Post by philinux on 2007-08-13
How embarrasing 

what a difference a capital x makes.

:lolflag:

---

### Post by stefanstefanstefan on 2007-08-13
I have WIndows and Ubuntu installed on my computer.
At this point, when I start my comuter, Ubuntu gets loaded, and if I want to start Windows, I have to manually select it.
How do I get to have the computer to start Windows by default?

---

### Post by igknighted on 2007-08-13
(1) this is a new issue, please start a new thread

(2) in this new thread, please post the entire output of the command ```
cat /etc/boot/menu.lst
```

(3) basically, what you will need to then is edit the file listed above (menu.lst) in the method outlined in this thread (using gksudo/sudo) and change the line that currently reads "default 0" to a new number corresponding with the line windows is on.  There are some catches, so post the output of the above command and ask for help (or, if you rather, a quick forum search could probably help you figure out what the "default" line should read).

---

