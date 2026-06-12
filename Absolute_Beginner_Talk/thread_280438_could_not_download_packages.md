---
title: "could not download packages"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by r3mu on 2006-10-19
hi..i'm a no0bie to ubuntu and i need some help here..i've tried googling but and i managed to solve some of the probs but there's other that i can't..can anybody help?..when i run apt-get update, i got this kind of error..

```
sudo apt-get update
Get:1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Get:2 http://packages.freecontrib.org dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://packages.freecontrib.org dapper Release.gpg [189B]
Get:5 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://wine.budgetdedicated.com dapper Release.gpg
Hit http://packages.freecontrib.org dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://wine.budgetdedicated.com dapper Release
Hit http://packages.freecontrib.org dapper Release
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Get:6 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:7 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://archive.ubuntu.com dapper Release
Hit http://wine.budgetdedicated.com dapper/main Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 383B in 24s (16B/s)
Failed to fetch http://packages.freecontrib.org/plf/dists/dapper/Release  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

and when i'm using synaptic's i got this error

```
http://packages.freecontrib.org/plf/dists/dapper/Release: Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)

```

how can i fix the probs?..thanx in advance..

---

### Post by jordanmthomas on 2006-10-19
The PLF repos never seem to work properly.  I would just disable it in Synaptic or comment it out in sources.list.

---

### Post by Marsolin on 2006-10-19
That looks like a repo problem and not a problem on your end.

---

### Post by r3mu on 2006-10-19
any suggestion to fix?..

---

### Post by SSamiK on 2006-10-19
in a terminal:
sudo gedit /etc/apt/sources.list 
and put a # in front of [http://packages.freecontrib.org/plf/dists/dapper/](http://packages.freecontrib.org/plf/dists/dapper/) (or simply delete that line)

---

### Post by r3mu on 2006-10-20
but i don't have that line in my sources.list..this is my sources.list...
```
deb http://packages.freecontrib.org/plf dapper main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb http://packages.freecontrib.org/plf dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
##MAJOR BUG FIX UPDATES
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
##UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
##BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
##PLF REPOSITORY
deb http://packages.freecontrib.org/plf dapper free non-free
#deb-src http://packages.freecontrib.org/plf dapper free non-free
##CANONICAL COMMERCIAL REPOSITORY
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://wine.budgetdedicated.com/apt dapper main

```
thanx in advance..

---

### Post by jordanmthomas on 2006-10-20
```
##PLF REPOSITORY
[COLOR="Red"]#[/COLOR]deb http://packages.freecontrib.org/plf dapper free non-free
#deb-src http://packages.freecontrib.org/plf dapper free non-free
```
Put a # where I have put the red one.

---

