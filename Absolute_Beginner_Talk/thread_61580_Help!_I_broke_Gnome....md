---
title: "Help! I broke Gnome..."
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-09-01
[http://www.ubuntuforums.org/showthread.php?t=20769&highlight=xcompmgr](http://www.ubuntuforums.org/showthread.php?t=20769&highlight=xcompmgr)

I followed this how to, in order to enable xcompmgr and set some shadows to my windows (I wanted to play with some eye candy).  now however, each time I try to boot into Ubuntu, the loader that says things like "starting nautalis, configuring gnome etc" hangs as it says it's loading the updater....

I need to know how to revert what I have done, most likley in recovery mode as I can't get into gnome at all!

No silly shadows are worth this,,,

---

### Post by KingBahamut on 2005-09-01
Uninstall xcomp and its dependencies. Remove the .xcomp entries in home, comment out your changes in xorg.conf , then reboot.

---

### Post by the_purulent on 2005-09-01
I would, but I cannot load into ubuntu.  It hangs on the load screen.  Is there a way I can do it from the recovery console?

---

### Post by izmaelis on 2005-09-01
What video card and what driver do you have installed on your system?

---

### Post by the_purulent on 2005-09-01
I have an nvidia 4600ti
I'm unsure as to the driver version, but I did the driver update as per the ubuntu guide... roughly 4 weeks ago.

Basically if there is a way I can edit the programs that run on startup from the recovery terminal then I think I would be all set,,, I could then stop the offending program from running and remove it when I boot back up.

---

### Post by izmaelis on 2005-09-01
I have GeForce FX5600XT working on 7676 nVidia driver version and somehow xcompmgr doesn't work. When graphical server starts up system just locks up with no response. I had to disable all shadows etc.
P.S. Everything worked just fine with an older (Ubuntu) nVidia driver. So I gues you should follow workarround given by KingBahamut.

---

### Post by the_purulent on 2005-09-01
Ok, what can I use to edit xorg.conf without being in gnome (basically just have a black screen with a terminal, so no access to gedit)?  If I can get in there I can fix it.

---

### Post by Wolki on 2005-09-01
[QUOTE=the_purulent]Ok, what can I use to edit xorg.conf without being in gnome (basically just have a black screen with a terminal, so no access to gedit)?  If I can get in there I can fix it.[/QUOTE]

nano.

just run sudo nano /etc/X11/xorg.conf

there are other command line text editors, but nano is the easiest.

to get to a console, boot ubuntu in failsafe mode - or - boot it the normal way and then hit ctrl-alt-F1 when X is up.

---

### Post by the_purulent on 2005-09-01
PERFECT!
Thank you Wolki! That was exactly the answer I was looking for :)
Failsafe mode did the trick!

---

### Post by Wolki on 2005-09-01
I'm glad it worked.

Glancing over the thread again i noticed this:


[QUOTE="the_purulent"]No silly shadows are worth this,,,[/QUOTE]

And i just wanted to say that xcompmgr is more than shadows, more than translucent windows and more than the (great looking but with time annoying) fades. The best part of it -in my opinion - is xdamage.

Say you open a text file. Then you put another window on top of that, like a file manager window. Now when you move that window there will be a short time when that part of the text window will be blank until it is redrawn. It's even worse with firefox, where you will see window trails, very ugly. With xcompmgr running it's not completely solved, but it redraws almost instantly, any delay is hardly noticable. Makes the whole system feel much faster.

---

