---
title: "Opps!!!"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by g33knik on 2006-12-08
:( I am a n00b to linux. I recently installed Unbuntu 6.1, got my wi-fi wpa working and Enemy Territory, thanks to the help of the friendly people on these forums. Well, I was having an issue whenever I updated Unbunu. I kept getting this message about something-graphviz-cairo.....error 127 or something. I tried "fixing" broken packages and all that but nothing changed. Well, I noticed that this cairo thing was associated w/ python, and being a brain-washed Windows user for do long I figured if I "uninstalled" python and reinstall maybe that would work. LOL.....well NOW all I get is the terminal prompt. (I figured at the time it was a bad idea, removing python...but well, thats why I'm using linux, so I can learn it). I can run startx but all that gets me is a blank desktop w/ a cursor and a console. I have tried the apt-get upgrade python but it doesn't fill in the blanks of all the files I need for a complete desktop that I in error, removed. Any thoughts on this before I just do a fresh reinstall of Ubuntu and start completely over?

---

### Post by scc4fun on 2006-12-08
> **g33knik said:**
> :( I am a n00b to linux. I recently installed Unbuntu 6.1, got my wi-fi wpa working and Enemy Territory, thanks to the help of the friendly people on these forums. Well, I was having an issue whenever I updated Unbunu. I kept getting this message about something-graphviz-cairo.....error 127 or something. I tried "fixing" broken packages and all that but nothing changed. Well, I noticed that this cairo thing was associated w/ python, and being a brain-washed Windows user for do long I figured if I "uninstalled" python and reinstall maybe that would work. LOL.....well NOW all I get is the terminal prompt. (I figured at the time it was a bad idea, removing python...but well, thats why I'm using linux, so I can learn it). I can run startx but all that gets me is a blank desktop w/ a cursor and a console. I have tried the apt-get upgrade python but it doesn't fill in the blanks of all the files I need for a complete desktop that I in error, removed. Any thoughts on this before I just do a fresh reinstall of Ubuntu and start completely over?
try doing ```
sudo aptitude install ubuntu-desktop
``` This will keep your install in place but install only what is needed for the Gnome desktop to work. If you use Kubuntu or Xubuntu then add the k or x to the beginning of ubuntu-desktop so it is kubuntu-desktop or xubuntu-desktop.


[http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

---

### Post by civic_si on 2006-12-08
if you uninstalled python then you need to reinstall not try to upgrade python. try 

sudo apt-get install python

see if that fixes it.

---

### Post by infoseeker on 2006-12-08
have you tried```
sudo apt-get install ubuntu-desktop
```
EDIT - OOPS double post

---

### Post by g33knik on 2006-12-08
=D> :biggrin: Than you very much. I did try reinstalling python which didnt work. It installed but didnt fix my problime. I will get the desktop though and let you all know if it worked. Thanx a bunch.:cool:

---

### Post by g33knik on 2006-12-08
:KS :KS :KS :KS :KS That worked! I ran apt-get install ubuntu-desktop and voila! Again thank you! \\:D/ \\:D/ \\:D/

---

