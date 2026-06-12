---
title: "Software installation: WINE (was: nubee need help)"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by in2media on 2006-09-24
when i had suse 10.0 on my other pc (before the kids put xp back on) i used to use yast and packman to install software
is there something similar on ubuntu
also is wine easy to set up on ubuntu, i tried it on suse but never got it working:D

---

### Post by bodhi.zazen on 2006-09-24
That's noobie.

---

### Post by bodhi.zazen on 2006-09-24
> **in2media said:**
> when i had suse 10.0 on my other pc (before the kids put xp back on) i used to use yast and packman to install software
is there something similar on ubuntu
also is wine easy to set up on ubuntu, i tried it on suse but never got it working:D

Yes, ubuntu uses apt-get, aptitude, and/or synaptic. apt-get and aptitude are CLI.

edit /etc/apt/sources.list to enable repositories.

Wine is no easier or hareder on Ubuntu then SUSE.

---

### Post by in2media on 2006-09-24
im not a noobie im a nubee

---

### Post by in2media on 2006-09-24
thanx il take a look at that:p

---

### Post by xpod on 2006-09-24
Here you use "synaptic" or "add\remove"(choosing advanced mode on this switches to synaptic)

There`s also the command line which is even easier once you learn the basics but you probably already know the linux basics so this should come a bit easier mabey????

In "synaptic" you should go to "settings" and then repositries then click "add" and check the empty boxes to enable the extra repositries which will give you close to 20,000 apps to chose from:D

EDIT...trust the irish to get there before me:D

---

### Post by bodhi.zazen on 2006-09-24
u b nu b 2

---

### Post by in2media on 2006-09-24
thanx,il have a go at it tomorrow when im in my workshop

---

### Post by in2media on 2006-09-24
u b nu b 2
__________________
yeah i b nu 2 buntu but not 2 linux

---

### Post by xpod on 2006-09-24
u r 2 u su:D

---

### Post by in2media on 2006-09-24
> **xpod said:**
> Here you use "synaptic" or "add\remove"(choosing advanced mode on this switches to synaptic)

There`s also the command line which is even easier once you learn the basics but you probably already know the linux basics so this should come a bit easier mabey????

In "synaptic" you should go to "settings" and then repositries then click "add" and check the empty boxes to enable the extra repositries which will give you close to 20,000 apps to chose from:D

EDIT...trust the irish to get there before me:D

do i need to type in the repositries, if so where can i find em

---

### Post by xpod on 2006-09-24
see my last sensible post for how to enable the extra repo`s

OR you can do it a number of other ways but thats generally the easiest way to start off:D

---

### Post by in2media on 2006-09-24
sorry i didn't read it right, was upset being called noobie.:( dont think il ever get over that, told wife to hide the sharp knives

---

### Post by xpod on 2006-09-24
LOL....Dont let ANYTHING you hear from our irish friend upset you.....he`s still a nubee and has yet to find his feet...lol

Be kind to him...he`s a good old sort:biggrin:

EDIT: i heard his ISO took 8 weeks to download so they backdated his bean count and entry date for him

---

### Post by in2media on 2006-09-24
sounds more fun on this site then any of the other linux sites ive used
thanx for the help il give it a go tomorrow

---

### Post by Brunellus on 2006-09-24
thread title has been changed to better reflect nature of help request.  In the future, please use the thread title to state briefly the type of problem you need help with.  This will allow users who know how to help you to know that they can help you.  Simply posting:  HELP THIS NEWBIE may elicit pity, but seldom useful technical advice. 

The WINE project provides excellent directions for installing their latest binary builds of WINE:

[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

As to installing other software generally in Ubuntu, please see

[https://help.ubuntu.com/community/InstallingSoftware?highlight=%28installing%29](https://help.ubuntu.com/community/InstallingSoftware?highlight=%28installing%29)

---

### Post by comppsyco on 2006-09-24
One more thing:
PLEASE USE APTITUDE. It is much better than apt-get. (from [www.psychocats.com](www.psychocats.com))
The advantages of aptitude over apt-get
aptitude has an important feature that its command-line cousin apt-get and the graphical frontends Synaptic and Adept do not have--it remembers dependencies. If you update with aptitude, install with aptitude, and then uninstall with aptitude, all the dependencies you installed with a particular package will be removed when that package is removed (unless other packages also depend on those dependencies). If you install with Synaptic, Adept, or apt-get, uninstalling will uninstall only the package you specify--not the dependencies that came with it.

For example, if you install kword, you will also install kspread, kword-data, and libwv2-1c2. If you install kword with aptitude and then uninstall with aptitude, kspread, kword-data, and libwv2-1c2 will also be removed along with kword. If, however, you install kword with apt-get and then uninstall kword, kspread, kword-data, and libwv2-1c2 will remain installed, and you will not be prompted to remove them.

---

### Post by bodhi.zazen on 2006-09-24
> **in2media said:**
> sorry i didn't read it right, was upset being called noobie.:( dont think il ever get over that, told wife to hide the sharp knives

:lol: From one noob to another, or if you prefer one noob to ye ole wizened one, welcome to Ubuntu.

---

