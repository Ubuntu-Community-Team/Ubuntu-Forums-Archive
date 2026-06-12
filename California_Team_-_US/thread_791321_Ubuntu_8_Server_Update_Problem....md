---
title: "Ubuntu 8 Server Update Problem..."
date: 2008-05-12
forum: California Team - US
---

### Post by rhine08 on 2008-05-12
Hi everyboby!!! anyone can help me to solve this problem:

here is the situation, my internet connection is ok... then once i use the command apt-get update it says E: UNABLE TO LOCK DIRECTORY LIST, anyone of you can solve this?

Thanks and More power...

Note: I used Ubuntu 8 Server.

---

### Post by njparton on 2008-05-12
Are you trying to do more set of updates at a time or are you installing something at the same time as updating?

---

### Post by rhine08 on 2008-05-13
I'm a beginner for linux and this is my first time...

after i installed ubuntu 8 server i swith the user to root then i want to update but that error is found while in ubuntu 8 desktop is ok even terminal or gnome, the point is how to solve this error in server and update.

hoping for immediate response... thanks a lot ubuntu users...

---

### Post by Flannel on 2008-05-16
This error occurs when you're trying to use more than one package manager at the same time.  These include: apt-get, aptitude, adept, update-manager, add/remove (whatever the binary is named), synaptic, etc.

So, if you get this error, close any other package managers you're running, and if you're not running any, try waiting a bit, update-manager may be doing its thing on boot, and if you wait for it to finish, you'll be fine.

Also, don't use the root user.  Use sudo instead.

---

