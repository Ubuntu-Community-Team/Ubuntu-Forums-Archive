---
title: "[SOLVED] Xserver-xorg"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by wudze on 2007-11-16
Hi,  I just upgraded the distro and now when I try to load i get a message similar to "unable to start the xserver-xorg..."  I reboot and enter recovery mode and type "dpkg-reconfigure xserver-xorg" go through all the steps and I still just end up with a prompt for login:  I enter my username  and then my password and I'm denied.

Any Idea's?

---

### Post by rfruth on 2007-11-16
does startx work ?

---

### Post by wudze on 2007-11-17
Hi,  since the initial post i have tried the following :
sudo /etc/in.t.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
startx

issue remained, so I swapped out the video card and put in an ATI rage2c which I know works, used the same commands as above, issue remains.  I really hope that I dont have to flatten and re-install, I want to download and setup Ubuntu Studio, so this is getting annoying :-)

---

### Post by rsambuca on 2007-11-17
You upgraded from which version to which version?

---

### Post by wudze on 2007-11-17
I upgraded from dapper to gutsy.

new issue is now even the live CD fails and gives the same error about xserver-xorg, so I ran the sudo dpkg-reconfigure..... again and now I get the following message : "Fatal Server Error: no screens found XIO: fatal IO error 104 (connection reset by peer) on xserver ":0.0"

---

### Post by rsambuca on 2007-11-17
Was this a fresh install then?  Or did you go Dapper to Edgy to Feisty to Gutsy, because that is the only way the upgrade process will work.

---

### Post by wudze on 2007-11-17
nope it wasn't a fresh install, i've been running a couple of months, doing all the updates, then decided to run apt-get dist-upgrade, unit was working well for about a week, then 2 nights ago, turned it on and thats when I got no further than the reported errors.

---

### Post by wudze on 2007-11-17
anyone with a possible solution?

---

### Post by rsambuca on 2007-11-17
What is the output of uname -a?

The reason I am asking is that if you upgraded from Dapper, then you should be running Edgy, not Gutsy.  If somehow you went from Dapper straight to Gutsy, then your system will in all likelyhood be borked.

---

### Post by wudze on 2007-11-17
when I enter uname -a here's the response :

linux 2.6.15-23-386 #1 PREEMPT Tue may 23 13:49:40 UTC 2006 i6 86 GNU/Linux

---

### Post by wudze on 2007-11-17
I found the solution!!

sudo dpkg-reconfigure -phigh xserver-xorg  this got me into a basic desktop, I was unable to do a normal shutdown and restart so had to pull the power, unit started up, and so far so good.

I'd like to thank rsambuca for their input in helping to resolve this annoying issue.

---

