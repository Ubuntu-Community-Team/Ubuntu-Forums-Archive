---
title: "I recently made the switch, now for my problems"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Master-of-None on 2007-12-25
Alright guys, first of all, what I've gotten out of Ubuntu already eliminates Windows as one of my options, however, I'm not fully up to speed with what I got to understand.

First things first, the ATI accelerated graphics driver in the restricted drivers menu gives me the following error:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

this also comes up when I try to use the Add/Remove applications menu

I will admit the fault here, I tried to install a lot of stuff from the boot CD,and left some things unconfigured, but before that, it stated I needed xorg- something.
 applications are not 

Secondly, I don't know how to install things like Flash or Java,

---

### Post by taurus on 2007-12-25
Close Add/Remove or others apps that you have to install stuff.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by Master-of-None on 2007-12-25
Thank you very much! I didn't expect such a speedy response!

but now I have another problem. My Linksys wireless router isn't configured and I've tried to configure it via my Windows Desktop(family computer) but to no avail. The problem is that I don't have a spare ethernet chord, and I don't have the ability to get a new one until after January.

Is there a way to configure it via Ubuntu and my laptop?

---

### Post by shareMenaPeace on 2007-12-25
Hi, 
make sur eto enable 3rd Party Repos and Ubuntu Software under

Administration - >>> Software Sources 

Once you did this start

Administration ->>> Update Manager and run this

Than

Start Firefox and go to a flash website, this should ask you automaticly to install Flash-Plugin.

---

