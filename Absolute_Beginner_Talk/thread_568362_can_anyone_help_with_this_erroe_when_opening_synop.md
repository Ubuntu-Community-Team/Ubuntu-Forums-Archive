---
title: "can anyone help with this erroe when opening synoptic manager"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by tonym53 on 2007-10-05
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by overdrank on 2007-10-05
> **tonym53 said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Hi if you will run 
```
sudo dpkg --configure -a
```
In the terminal this will correct the error! Good luck!

---

### Post by Shazaam on 2007-10-05
Do what synaptic asked.
Open a terminal, type in 

sudo dpkg --configure -a

enter your password (blinking cursor will not move as you type, don't worry it's the default action for security), hit enter. Sometimes it will output code, most times it won't.
What this does is it configures unconfigured apps, with the -a flag (all) set.

---

### Post by tonym53 on 2007-10-05
worked a treat had to repair broken package now opens ok
thanks for your help

---

