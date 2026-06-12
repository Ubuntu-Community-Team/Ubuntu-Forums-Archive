---
title: "m new to ubuntu...help me out"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Devakishor on 2007-11-10
i got this error while installing softwares and updates

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 E: _cache->open() failed, please report."

i didnt have this problem before... 

also i installed beryl but i can't get it to work.. what could be the problem and how to get it working..

---

### Post by skymera on 2007-11-10
do as it says

dpkg --configure -a

---

### Post by matthewcraig on 2007-11-10
Did you run "dpkg --configure -a" ?  Sounds like your Internet connection was interrupted.

---

### Post by overdrank on 2007-11-10
> **Devakishor said:**
> i got this error while installing softwares and updates

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 E: _cache->open() failed, please report."

i didnt have this problem before... 

also i installed beryl but i can't get it to work.. what could be the problem and how to get it working..

HI and welcome, if you will run that command in the terminal ```
sudo dpkg --configure -a
``` that should correct the issue. the terminal is located under applications, accessories, terminal. Good luck!

---

### Post by Samanathon on 2007-11-10
I'm pretty new here too, but from what I can tell, you need to enter the following command into the Terminal (Application->Accessories->Terminal):

[INDENT]dpkg --configure -a[/INDENT]

As for your question: *also i installed beryl but i can't get it to work.. what could be the problem and how to get it working..* - this depends on what version of Ubuntu that you are running. 7.10 includes Compiz by default (Beryl is no longer supported). Check out this [**this how to]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")** for instructions on set up and config!

---

