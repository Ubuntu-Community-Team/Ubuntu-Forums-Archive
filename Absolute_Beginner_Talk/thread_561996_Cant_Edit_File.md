---
title: "Cant Edit File"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Conano on 2007-09-28
Each time i log into ubuntu, i have to change my video to a resolution of 1440x900. Each time i try and save that resolution to the xconfiguration file it tells me i dont have permission and wont let me save or amend the files nessicary. 

I tried logging into the root account, but it told me i couldnt log in from the log in screen... go figure. 

Anyideas?

---

### Post by anaconda on 2007-09-28
in ubuntu we use the sudo or gksudo command to temporarily get root rights.

eg. type this in terminal,( or Alt-F2 and type this there)
gksudo gedit /etc/X11/xorg.conf

(I assume that is the file you want to edit..)

---

### Post by Conano on 2007-09-28
yes. but why cant the nividia controle panel modify the file on it's own? i havent a clue where to put what otherwise i'd manually splce the files together myself.

This is what i got as a responce.... Think i may have screwed something up lol.... 

dmitry@dmitry-desktop:~$ gksudo gedit /ect/X11/xorg.conf
(gedit:8505): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by anaconda on 2007-09-28
Nah.. that "error" message is perfectly normal and harmless. I think it will come each time you (or anyone) uses gksudo.
If you dont want to see that message then use sudo instead. (gksudo is meant for starting graphical programs and sudo for nongraphical ones. While sudo works also for graphical programs..) 

but maybe what you really want is to start the nvidia-settings with root rights eg.
sudo nvidia-settings
would do that

---

