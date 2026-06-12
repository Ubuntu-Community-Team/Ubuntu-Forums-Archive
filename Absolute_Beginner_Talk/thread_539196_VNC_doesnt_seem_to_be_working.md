---
title: "VNC doesnt seem to be working"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by always4lora on 2007-08-30
hey there, ive recently got ubuntu 6.10 on my server, which i can currently only connect to via SSH, ive installed gnome and vncserver

when i do startvnc it says its started the server, when i log in with vnc all i see is  like an orrange bar saying ubuntu nothing can be clicked or anyhing. so seems like its working and its not at the same time

ive put exec gnome session at the end of my Xsession file.

Cheers Ben

---

### Post by arsya on 2007-08-31
How did you start the vncserver? Did you login to the ubuntu server via ssh, and then you start the vncserver (vino)? When you run vino,  did you export DISPLAY first?

As far as I know, when you login into GUI, such as gnome, then the vino (vncserver) will be started. So, you are trying to remote desktop the system before it is logged in to the GUI. And that's why you run the vncserver manually (or you put it in xsession).
I have tried similar case, without success.

---

### Post by always4lora on 2007-08-31
hey there, im starting it like i did when i had fedora which is by doing vncserver , on my old server doing this would startx and also start kde.

---

