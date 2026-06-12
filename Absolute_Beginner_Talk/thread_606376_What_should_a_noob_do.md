---
title: "What should a noob do?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by geedog on 2007-11-07
While installing flash plugin I got this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I dont know what to do... Im running Gutsy. Any help is welcome... Thanks

---

### Post by taurus on 2007-11-07
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Maestro23 on 2007-11-07
> **geedog said:**
> While installing flash plugin I got this message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I dont know what to do... Im running Gutsy. Any help is welcome... Thanks

Run the commands from a terminal:

> sudo dpkg --configure -a

sudo apt-get update

sudp apt-get upgrade

The Flash Plugin is available from the Reapositories;

> sudo apt-get install flashplugin-nonfree

---

### Post by geedog on 2007-11-07
OK Thanks I'll give it a try and let ya know

Thanks again

---

### Post by geedog on 2007-11-07
Igot this on the Flash install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Now what?

---

### Post by geedog on 2007-11-08
Thanks for the help. I got part of the problem solved. Had to fix a broken package in Synantic.   Got updates going again. Still cant get Flash,  Will tackle that tonight. 

See you then

Geedog

---

