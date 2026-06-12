---
title: "Is it safe to have automatix-installed applications if moving to dapper?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-25
if i want to do the dist-upgrade on june 1st, will my automatix-installed applications disrupt/mess up my upgrade?

---

### Post by linuxcity on 2006-05-25
Base on what I have heard, it is better to use EasyUbunt:


[http://easyubuntu.freecobntrib.org/get.html](http://easyubuntu.freecobntrib.org/get.html)

---

### Post by mr_ed on 2006-05-25
[QUOTE=erik1397]if i want to do the dist-upgrade on june 1st, will my automatix-installed applications disrupt/mess up my upgrade?[/QUOTE]

I doubt it.  One thing you could do is make your /etc/apt/sources.list file (aka Repositories in Synaptic) identical to the ones that would come in a vanilla Dapper install.
After doing that, do an update and then dist-upgrade.

---

### Post by aysiu on 2006-05-25
According to arnieboy (the author of Automatix), there should be no adverse effects.

---

### Post by user1397 on 2006-05-25
okay thanks everyone this really saved me some would-be stress;)

---

### Post by cstudent on 2006-05-25
I have a old system at work I use to play with that I just did a dist-upgrade on a few days ago. It had some applications that I used Automatix to install them. I've had no problems so far with it. It shouldn't be a problem. All Automatix is really is a bash script that automates installation of packages via apt-get. You could use the terminal and do exactly the same thing Automatix does by entering each apt-get command one at a time. Any packages that were installed using Automatix will get upgraded if an upgrade is available in the repositories that are in your sources.list for Dapper. 


.

---

