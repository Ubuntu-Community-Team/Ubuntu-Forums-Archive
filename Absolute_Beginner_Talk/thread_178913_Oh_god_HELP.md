---
title: "Oh god HELP"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by the fish on 2006-05-18
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found

This keeps coming up. What does it mean??

---

### Post by xXx 0wn3d xXx on 2006-05-18
[QUOTE=the fish][http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found

This keeps coming up. What does it mean??[/QUOTE]
It means that you can't connect to those repositories, everything is fine. Just type this in terminal (Applications > Accessories > Terminal).

> sudo gedit /etc/apt/sources.list

Look for those lines and put a # in front of them. Just those lines.

# [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)
# [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:)

---

### Post by Dr. Nick on 2006-05-18
[quote=the fish][http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:]("http://koti.mbnet.fi/%7Eots/ubuntu/breezy/Packages.gz:") 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:]("http://koti.mbnet.fi/%7Eots/ubuntu/breezy/Sources.gz:") 404 Not Found

This keeps coming up. What does it mean??[/quote]

If it comes up when you are messing with synaptic or apt-get it means the site is down so it cant install from it.

Edit the file /etc/apt/sources.list or jsut edit repositories in synaptic to remove it.

---

### Post by Sef on 2006-05-18
Seems like they are in your source list and can't find the right directory.

Are you using Ubuntu or Kubuntu?

---

### Post by the fish on 2006-05-18
Ubuntu

---

### Post by Sef on 2006-05-18
> Ubuntu

Then just follow the directions from MasterinChief.

---

### Post by the fish on 2006-05-18
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/ 
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) stable main

## created by arnielistenremoved

those line are not there

---

### Post by Sef on 2006-05-18
> deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

I would comment out those two lines by adding a # before them.  Those lines should look like this now:

> 
#deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
#deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/


Note: They are at the bottom.

---

### Post by mlind on 2006-05-18
see [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by cstudent on 2006-05-18
You can also manage the sources.list by going to the menu System>>Administration>>Software Properties. Then just uncheck the repositories you don't want to use. 



.

---

