---
title: "can't figure out root password"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by hwdoyle on 2007-03-12
Hello everybody, 
I've just installed ubuntu 6.10 desktop version (had this same problem with earlier versions too). It never asks me to supply a root password during the install. When I get up and running and reboot into the fresh install, I log in with my initial username/password that i set up during the install process, but i cannot sudo to root. This has happened a couple of times to me - what am i missing?
Thanks!
Harry

---

### Post by arron on 2007-03-12
root by default is disabled, to the best of my understanding.  Run

sudo *command to run*

to run it as root, the password is your user password.  If you want a root prompt *be carefull here*

sudo -i

i is for interactive.  I was used to having a root login, but aftr getting used to this, i like the sudo aproach it has saved me a couple times from some command mistakes that could of cost me time.

---

### Post by siciliancasanova on 2007-03-12
[This thread]("http://ubuntuforums.org/showthread.php?t=363107&highlight=root+password") has a lot of descriptions on how to use root.

It looks like you might have to go into recovery mode on the boot and enter this:```
adduser *your user name* admin
id *your user name*
```

---

### Post by Bachstelze on 2007-03-12
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by daddydoc on 2007-03-12
try ubuntu

---

