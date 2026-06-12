---
title: "Uh Oh, what'd I do?!"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by tiggertiffin87 on 2005-11-23
I installed Ubunto 5.10 yesterday (Breezy I guess would be the version).  Today I updated stuff and installed some packages and restarted my system.  Now instead of going to the Gnome login screen I get:

Ubuntu 5.10 "Breezy Badger" (username) tty1

(username) login:

I enter my user name and password then I just get (username)$ or something like that.  How do I get into Gnome again??  Do I have to reinstall?  I'm so lost! :oops:

---

### Post by matthewv on 2005-11-23
I can tell you what you have done, even if I cant tell you the solution.
You have mucked up the config for your graphics server. Try a ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tiggertiffin87 on 2005-11-23
Okay I tried that.  I got to the part asking to select a color quality and I selected 24.  When I hit OK I get:

xserver-xorg postinst warning: overwritting possibly-customised configuration file; backup in /etc/X11/xorg.conf. 200511230110
(loginname)@(username):~$

What now?

---

### Post by matthewv on 2005-11-23
try typing ```
startx
```to try starting you xserver (graphics server) If it works, a restart should bring up a graphical login screen, if it doesn't work, please post the error message here

---

### Post by Gustav on 2005-11-23
I had the same experience this morning. 

For me it was because i had updated my kernel but not the nvidia drivers. If you have a pretty old nvidia (GeForce2 or older) and you use the nvidia-legacy drivers, you have to install linux-restricted-modules-2.6.12-10-<your_processor_type>-nvidia-legacy
(replace <your_processor_type> with 386, 686, 686-smp, k7 or k7-smp)

---

### Post by tiggertiffin87 on 2005-11-23
So, um, how do I do that? :D

By the way, it's an Nvidia GeForce 2Ti

Okay, nevermind, I figured it out.  Cross your fingers for me!

---

