---
title: "freenx uninstall"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-17
i installed freenx following some tutorial on this forum(can't remember which one) and i want to uninstall it.
the problem is that i was using apt-get so dependenicies are going to stay if 
i use apt-get remove.

installed packages are : freenx nxclient nxplugin
i just need to now what are the dependenices that i can safely remove from my system. i want to keep it clean.

a perfect solution would be if someone installed the above packages using aptitude so a simple: 
**sudo aptitude remove freenx nxclient nxplugin** and the output of the commmand would make my penguin very happy  :)

---

### Post by capn_hector on 2006-10-17
uninstalling the program is fine but why would you want to remove the dependices.  the dependencies are simaler to shared dll's.  most you can remove but i tend to leave them on my system.  if your worried about space and want them off, do an apt-get remove then an apt-get install and it will check for dependencies.  write down what those are and then do an apt-get remove on every thing.

---

