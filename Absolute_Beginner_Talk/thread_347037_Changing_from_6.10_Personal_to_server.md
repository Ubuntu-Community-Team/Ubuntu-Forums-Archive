---
title: "Changing from 6.10 Personal to server"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by proxima estacion on 2007-01-26
Hi,

I Have Edgy working fine, I want to set up a personal web server and think maybe I should have gone with ubuntu server in the first place. can I just download the necessary parts to change personal into server or am i better off doing a clean install of Server edition?

Thnaks

---

### Post by taurus on 2007-01-26
If you want to make your Ubuntu box into a web server, then just install apache2 and it will be a web server and you still have Gnome window manager to play around with.  

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install apache2
```

---

### Post by Frogger on 2007-01-26
What do you want to do with it?  If you are just looking to run a webserver, on the web, you should switch.
You could easily get all of the software from the server install individually and configure it yourself, but the benefit of a server install is that out of the box nothing is running and the bare minimum is installed.  Out of the box it does not even have a GUI.
If you use your system every day then don't install the server install, unless you really like the command line.  My general rule is if the system's primary input is not ssh, I do not use server.

---

