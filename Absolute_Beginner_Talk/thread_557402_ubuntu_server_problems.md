---
title: "ubuntu server problems"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by killagorilla1 on 2007-09-22
ok i just installed ubuntu server and all seemed to go well
it went all the way through the setup, then rebooted,then asked for userid and password. after i enter them in it gives me a new line like this

pc@~$ 

pc is just what i called the machine

any ideas?

---

### Post by julian67 on 2007-09-22
That's what it is supposed to do. You're logged in to your new server. if you want a desktop environment instead of using the terminal you will need to install and configure one.

---

### Post by overdrank on 2007-09-22
> **killagorilla1 said:**
> ok i just installed ubuntu server and all seemed to go well
it went all the way through the setup, then rebooted,then asked for userid and password. after i enter them in it gives me a new line like this

pc@~$ 

pc is just what i called the machine

any ideas?

HI the server edition does not come with a GUI if you would like to install one just use the command
```
sudo apt-get install ubuntu-desktop
```
Or replace ubuntu with kubuntu if you choose to use KDE

---

