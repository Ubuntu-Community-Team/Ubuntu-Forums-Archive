---
title: "[SOLVED] VNC Server / VNC Client -syncing the  screen"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by xelnaga666 on 2007-08-15
hey there guys, Im looking for help with a Kubuntu vncserver. So far, with the client I have managed to connect to it tunnelled with ssh successfully. I have the gui pop up with just a grey screen and terminal though. Id like to be able to view the server (which is a laptop) in real time (as in for example, I move the mouse on vnc, it moves the pointer on the laptop screen). Any ideas how to achieve that?

---

### Post by bodhi.zazen on 2007-08-15
how did you connect ?

Take a look at x11vnc

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

---

### Post by xelnaga666 on 2007-08-15
Sweet!!! Many many many thanks!

Before I was using 'xtightvncviewer' (via ssh) on the client and vncserver on the server.

Now running x11vnc on the server instead of vncserver, seems to map the currently running x display perfectly, the way I want it to.

Again, many thanks!

---

