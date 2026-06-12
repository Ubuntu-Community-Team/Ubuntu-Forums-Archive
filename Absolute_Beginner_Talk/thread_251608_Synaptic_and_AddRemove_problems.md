---
title: "Synaptic and Add/Remove problems"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by longissor on 2006-09-05
When i try applying the software I mark I am always unable to connect with the repository. Why is this? And how can I fix it?
Thanks.

---

### Post by longissor on 2006-09-05
Oh and yeah, my internet connection is working.

---

### Post by jd65pl on 2006-09-05
Check your repositories see [this]("https://help.ubuntu.com/community/Repositories/Ubuntu") for more info on adding repositories

If you need more help post the info contained within /etc/apt/sources.list 

To do this open terminal and type

```
sudo gedit /etc/apt/sources.list 
```

---

### Post by sportsblue on 2006-09-06
I am also a new linux user and have the same problem (cannot download repositories through Add/Remove Applications or Synaptic).  I have a working internet connection through Firefox and a broadband ADSL router/modem.

If you can help it would be really appreciated.

Here is my etc/apt/sources.list as requested in the previous post:

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by WalmartSniperLX on 2006-09-06
Did you guys enable all the software channels (check em all) in the System/Administration/Software Properties ?

---

### Post by sportsblue on 2006-09-06
I had checked all the packages in Software Properties.

After some extra searching around (including:  [http://www.ubuntuforums.org/showthread.php?t=250832](http://www.ubuntuforums.org/showthread.php?t=250832)) I found out it was a DNS problem.

To fix I removed my router IP address from the DNS list (how did that get there :o), and checked that my ISPs DNS addresses were already set in System>Admin>Networking; DNS tab.

Thanks for your help (everyone) :D

---

### Post by jd65pl on 2006-09-07
Glad you got it sorted

---

