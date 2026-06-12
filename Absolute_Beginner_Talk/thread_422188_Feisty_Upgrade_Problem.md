---
title: "Feisty Upgrade Problem"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by nygex on 2007-04-24
I am trying to upgrade from Kubuntu Edgy to Feisty and I get the following message each time:

Failed to fetch [http://apebox.org/badgerexplosion/./Packages.gz](http://apebox.org/badgerexplosion/./Packages.gz) 301 Moved Permanently
Failed to fetch [http://blognux.free.fr/dists/debian/unstable/binary-i386/Packages.gz](http://blognux.free.fr/dists/debian/unstable/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://blognux.free.fr/dists/debian/main/binary-i386/Packages.gz](http://blognux.free.fr/dists/debian/main/binary-i386/Packages.gz) 404 Not Found

Everything is up to date but I am not sure what I need to do to resolve this issue.  It shuts down the upgrade process each time.

Thanks

---

### Post by tchoklat on 2007-04-24
it is trying to access files that are not available. Try looking in your sources.lst and disable reference to these sites and see if that helps!

---

### Post by zvacet on 2007-04-25
You should comment unofficial repos during upgrade.That is for next time and right now try
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by bubbalouie on 2007-04-25
I'd say the other guys are on the money, to access your sources list try:

```
sudo kate /etc/apt/sources.list
``` (for kubuntu)

or

```
sudo gedit /etc/apt/sources.list
``` (for ubuntu)

or

```
sudo nano /etc/apt/sources.list
``` (for everything including the recovery console)

Here are the contents of my sources list (which works well BTW):

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END


```

---

### Post by nygex on 2007-04-25
Wow, thanks for all the replies.  Everything is working fine now.

---

