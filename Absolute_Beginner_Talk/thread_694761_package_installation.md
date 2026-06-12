---
title: "package installation"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by jsentianus on 2008-02-12
I tried to install some packages as I couldnt find them in synaptic packages but got the following error. Anyone can suggest what should I do.


sentian@dell:~$ sudo apt-get install build-essential bison byacc flex gawk g77 g++ libxt-dev tcsh tk8.4-dev xorg-dev libcurl4-dev curl gfortran
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
sentian@dell:

---

### Post by emarkd on 2008-02-12
Do you have Synaptic open at the same time?  You can't do both at once.

---

### Post by taurus on 2008-02-12
If you have synaptic open, close it down first before you run apt-get from a terminal.

---

### Post by mikewhatever on 2008-02-12
Close Synaptic window and try the command again.

---

