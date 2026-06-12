---
title: "What is the command to auto reconfigure the package/X-server settings?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-11-03
I broke a bunch of things last night trying to install Beryl.  i am up and running, and the only thing I can see that is still wrong is my sound is not very loud, but I want to make sure everything is back to how I started.  Is there a command to reset everything to how Edgy would have found it in the install process?  I did run through the reconfiguring of the X server last night as part of trying to fix my problems, but I know I messed some things up with the choices it was giving me (Not sure of what to pick).  Anyways, I am hoping for some type of automatic command if there is one to let the system reconfigure itself.

---

### Post by Architeuthis on 2006-11-03
The command to reconfigure the x-server is 
>  sudo dpkg-reconfigure xserver-xorg


If you want the standard options just choose autodetect from start and press enter every time. Then it should use all the standard options which ubuntu chooses during install (i did it several times when i messed up my xserver and it brought me back to standard every time).

---

### Post by tom56 on 2006-11-07
Im having a similar problem. The command given does offer the option to autodetect. How can I autodetect like the install CD did? The installer CD guessed everything perfectly, so what command was it using?

---

### Post by pastorjay on 2006-11-07
I am not sure what command it was using.  I just went through the list of things in the reconfiguration and pushed let it choose the options and then I hit ok.  Everything worked fine from there.

---

