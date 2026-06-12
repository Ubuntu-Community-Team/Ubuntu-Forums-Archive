---
title: "Remote Desktop to different user name"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by jsmkbunch2000 on 2007-07-16
I'd like to know if I can stay logged in as one user locally, however when I VNC in from work or elsewhere, can I remote desktop into another user name on the same machine without logging the current user off....

ie - logged in as "jenny1" and say my wife is using the computer.   I want to remote into my user account "john1" without interrupting her or even without her knowledge.  Is it possible to do this?

---

### Post by charles.g.moore on 2007-07-16
> **jsmkbunch2000 said:**
> I'd like to know if I can stay logged in as one user locally, however when I VNC in from work or elsewhere, can I remote desktop into another user name on the same machine without logging the current user off....

ie - logged in as "jenny1" and say my wife is using the computer.   I want to remote into my user account "john1" without interrupting her or even without her knowledge.  Is it possible to do this?

You should be able to do this since when you VNC in it should kick you to the login screen where you can enter another users account.

This post may help:
[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

---

### Post by jsmkbunch2000 on 2007-07-16
When I VNC, it takes me automatically to the Desktop of the user name I installed it on, however, it wont let me select or do anything unless it is logged in already locally.  then i can remote desktop.  It never takes me to the login screen to choose a login.  perhaps I need to install the vnc server differently?

---

### Post by Al3xK3aton on 2007-07-16
It works similarly to quick user switching on Windows except it's on Linux instead.

---

### Post by charles.g.moore on 2007-07-17
> **jsmkbunch2000 said:**
> When I VNC, it takes me automatically to the Desktop of the user name I installed it on, however, it wont let me select or do anything unless it is logged in already locally.  then i can remote desktop.  It never takes me to the login screen to choose a login.  perhaps I need to install the vnc server differently?

Im not sure but with vncviewer you could try passing the -display flag which would kick you into another xsession (i think)

man vncviewer (or whatever vnc app you are using)

---

### Post by jsmkbunch2000 on 2007-07-17
Is there a way to have i user using the desktop locally logged in as (ie- ) jane1 and for me to remote desktop (VNC) in and log in simultaneously to my own user name account without disturbing the desktop user (or even letting them be aware that I am logged in and using the desktop?

Another Scenerio:  

At Home: Wife on PC surfing Web
Me at Work: Log into Remote VNC user account to home PC with a different username without wife knowing about it or interrupting her.  - say to look up anniversary stuff privately or even surf porn etc...  (not that I surf porn, but you get the idea).  

The above responses dont tell me any how to's, please remeber I am new to Linux/Ubuntu and need step by step explinations.  

I think what I did was nstall the VNC onto my current username and instead should of installed the vncserver onto a root or main directory (not that I know how???) so that it would take me to the primary username and password screen like when I first turn on my computer????

---

### Post by Al3xK3aton on 2007-07-17
If you want to spy on your wife, there are easier ways to do it. You can get a spy camera for really cheap online, or install a keylogger when she's not home.

---

### Post by charles.g.moore on 2007-07-17
Which vnc app are you using???

---

### Post by jsmkbunch2000 on 2007-07-17
Not looking to spy on my wife.  I just want to log into my own username from work without having to log off the current logged in desktop user.  This away I can keep 1 user always logged in at home that they can use whenever and simoltaneously log in remotely from work or my laptop or where ever remotely without chenging the user currently logged in on the PC.  

I am not sure how to tell which version of VNC I am using on Ubuntu.  How do I paste this info to you?

---

### Post by charles.g.moore on 2007-07-18
do you use the gui to launch your vnc viewer?

if so, what is the name of it?

when you launch the app what is the name on the title bar of the window?

if you use the command line what is the name that you launch it with?

---

