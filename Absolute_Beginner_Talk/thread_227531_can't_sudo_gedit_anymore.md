---
title: "can't sudo gedit anymore"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by rlynch on 2006-08-01
so I wanted to edit my /etc/hosts file, but when i do 'sudo gedit /etc/hosts' in a terminal it just goes to a new line/bash

with no gedit opening up. . .
i am new to ubuntu, and am lost trying to setup apache, php, and mysql. for some reason apache isnt wanting to work correctly


any ideas on why i can't edit files like this anymore?

---

### Post by taurus on 2006-08-01
See if this works, from a terminal also...

```

sudo nano /etc/hosts

```

---

### Post by Indras on 2006-08-01
Before giving up, try this first:
1. Press Alt-F2 to bring up the Run menu
2. Type in "gksudo gedit /etc/hosts"

If it brings up a box asking for your password and then doesn't do anything after you enter it, something is wrong with gedit.  If it doesn't bring up the box at all, there's something wrong with sudo.  I've had a problem where sudo stopped working after changing the time on my clock (I found out from error logs that it kept throwing an error about authorization times being in the future).  I just had to restart to fix that.

---

### Post by T700 on 2006-08-01
There's probably a stalled instance of gedit running in the background.  Open up a terminal and type: ```
sudo killall gedit
``` and press Enter.  If that doesn't get things working, close your session and log on again.

Good luck!

Paul

---

### Post by rlynch on 2006-08-01
There were no previous gedit processes. I did a 'ps-ef | grep gedit' to check

The sudo nano command seems to work.

Thanks again

---

### Post by cuplex on 2006-11-04
hi, im not sure if you already fixed your problem!?

well i had the same problem but when i used the sudo gedit command it gave ma an error it can not load some icons! 
i checked the folder /usr/share/icons/gnome/
i could find all sizes but 36x36 and that was exatcly the size my gedit was missing! i dont know why or how to fix it easier...

is just copied the 32x32 folder to 36x36 folder and voila sudo gedit works^^

---

