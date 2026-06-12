---
title: "Backing up Settings"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by jbutler12 on 2006-12-20
hi all,

thanks to everyone for the help ive received in here.  After much work, I have ubuntu setup the way i want it, with wireless working, mp3 installed and working, pdf installed, all the firefox plugins i need, etc...  The computer im using is old, as is the harddisk in it.  I am worried about the harddisk maybe going bad since i had a boot error when i tried to restart (havent had one since) and i would love to be able to take a "snapshot" of my configuration and put it on a CD or something so that if i do need to do a fresh install of ubuntu i can just load all my settings and configurations.  Is there a utility to do this?

-John

---

### Post by repyzals on 2006-12-20
I suggest mondo rescue:

[http://www.mondorescue.org/](http://www.mondorescue.org/)

apt-get mondo
apt-get mondo-doc

---

### Post by aysiu on 2006-12-20
Your personal settings live in /home and your system-wide settings live in /etc

Back up those two folders.

---

### Post by chrisfay on 2006-12-21
I've been using partimage to create full images...Works great for me. My be overkill if you only need configuration settings saved. If so, aysiu posted the easiest method. 

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

