---
title: "MAJOR ISSUE!! graphical ui is gone"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by cvitullo on 2007-08-12
when i turn on my computer, it says "failed to start the X server (your graphical interface). It is likely that it is not set up correctly. would you like to view  the X server output to diagnose the problem?"

AAAAAAHHHHH!!!
help plz

---

### Post by aysiu on 2007-08-12
Press Enter until you get back to the terminal. Then, type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nonewmsgs on 2007-08-12
> **aysiu said:**
> Press Enter until you get back to the terminal. Then, type ```
sudo dpkg-reconfigure xserver-xorg
```

yes that definitely fixes the problem, but what i always wondered is how can the bootcd automatically detect the video card/moniter very well but then after a slight error in xorg.conf, it has to quiz the user instead of defaulting back to the original setup?

---

### Post by aysiu on 2007-08-12
> **nonewmsgs said:**
> yes that definitely fixes the problem, but what i always wondered is how can the bootcd automatically detect the video card/moniter very well but then after a slight error in xorg.conf, it has to quiz the user instead of defaulting back to the original setup?
"Bullet-proof-X" hasn't yet been implemented. We're hoping it makes it into the next release.

---

### Post by cvitullo on 2007-08-12
it says "sudo: dpkg-reconfig: command not found"

edit: oh wait, i'm a retard, wrong command. configure, not config

---

### Post by nonewmsgs on 2007-08-12
try 

cd /etc/X11 


(thats capital X) and then type it

cool aysiu

---

### Post by nalinde on 2007-08-12
well there shouldn't be any : in the command

---

### Post by cvitullo on 2007-08-12
yeah, i typed the command wrong, worked, rebooting

---

### Post by cvitullo on 2007-08-12
bleghh...  same error as initial post...

---

### Post by cvitullo on 2007-08-12
ok, says in the debug thing that no devices are found....

---

### Post by cvitullo on 2007-08-12
nvm, i'm just reinstalling from disc. easier

---

### Post by Arthur Archnix on 2007-08-12
> **aysiu said:**
> "Bullet-proof-X" hasn't yet been implemented. We're hoping it makes it into the next release.

:lol:

---

