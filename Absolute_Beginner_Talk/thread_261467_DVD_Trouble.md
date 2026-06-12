---
title: "DVD Trouble"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by greyhound on 2006-09-20
I have just loaded up UBUNTU for the first time. All seems to be working ok.
I have just put a dvd into the player and it wont play, tells me i need to install plugins, but does not say which plugins. Is there an easy fix for this. My computing skills are few and i could do with a little pointer.

---

### Post by maduranga on 2006-09-20
Installing these packages will help you to solve ur prob

libdvdcss2
libdvdread
libdvdplay
libdvdnav (for navigation)
win32codecs (optional)

these are the plug-ins u need. give the following command to install packages:

sudo dpkg -i "package name"

---

### Post by deadgobby on 2006-09-20
Hi and welcome to the world of Ubie. There is a reason why your DVD or MP3's will not play. One is that you need to install them your self and reasons why? Simple! Money... If Ubie had them all ready installed, it will no longer be free. So by your own hand you need to install the "Restricted Formats" There is a couple of ways to do this. One is to Dl and run Automatix [http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)
[http://www.getautomatix.com/](http://www.getautomatix.com/)
 You can install all the codecs with one sweep, but you need to read first before installing. Cause if you live in the states, it is illeagle, but no one is going to stop you. 
 To read up on restricted formats and how to install them.
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29)
 Once you have install them. Open up Synaptic and type in DVD in the search. There is several programs for DVD players and it is up to you which one you like.
Gobby

---

