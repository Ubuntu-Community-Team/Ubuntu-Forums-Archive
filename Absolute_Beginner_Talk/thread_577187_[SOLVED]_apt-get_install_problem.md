---
title: "[SOLVED] apt-get install problem"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-15
tttp@UBUNTU704:~$ sudo apt-get install conky
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  conky
0 upgraded, 1 newly installed, 0 to remove and 53 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
tttp@UBUNTU704:~$ 

how to solve this error  (Enable to lock  /var/cache/apt/archives/lock)?

---

### Post by aysiu on 2007-10-15
Close Synaptic Package Manager, Add/Remove, Update Manager, gDebi, or Adept Package Manager. Then try again.

---

### Post by mokkai on 2007-10-16
i closed those ....
the same problem  came again

---

### Post by mokkai on 2007-10-16
> **aysiu said:**
> Close Synaptic Package Manager, Add/Remove, Update Manager, gDebi, or Adept Package Manager. Then try again.

yes you are correct....
actually automatic updates is running in background (after that it ask me to restart the system )...

sorry for my inconvenience

anyway thanks....

---

### Post by FredB on 2007-10-16
Too late for me to answer :(

Anyway, thanks for the info, it could be useful ;)

---

