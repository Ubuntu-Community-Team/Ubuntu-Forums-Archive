---
title: "Can't get updates anymore"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by PLIACHAS PASCHALIS on 2007-12-02
Since i have installed 7.10 version to 3 Pc's which are in a local area i can't get anymore updates. But i have internet for all these Pc's.

If i run in a terminal "sudo apt-get update" i get the following message:" Unable to lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)

Any idea?
Thanks for help.

---

### Post by PmDematagoda on 2007-12-02
Do this:-

```
sudo rm /var/lib/apt/lists/lock
```

After that try:-

```
sudo apt-get update
```

---

### Post by PLIACHAS PASCHALIS on 2007-12-03
Thanks for your reply. i did this now it shows me that it tries to connect to the repo's but it remains to 0%.

---

### Post by OffAxis on 2007-12-03
Can you reach the internet with the three machines?

What does your /etc/apt/sources.list look like?

---

### Post by PLIACHAS PASCHALIS on 2007-12-03
as i said i can reach the internet.
THIS IS MY SOURCES.LIST FILE
# deb cdrom:[Ubuntu 7.04 "Feisty Fawn" - Release i386]/ feisty main restricted
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse

## Avant Window Navigator
# deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) Gutsy Gibbon avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) Gutsy Gibbon avant-window-navigator

# deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

---

### Post by PmDematagoda on 2007-12-04
Make a new sources.list file using [Source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/"), replace your old sources file using the new one **after** making a backup of the old one. Then try:-

```
sudo apt-get update
```

---

### Post by PLIACHAS PASCHALIS on 2007-12-04
I did what you told me and now i get this:
Error [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) gutsy Release.gpg                          
  Unable to connect to 2001:648:2000:de::211 (f=10 t=1 p=6) - socket (97 Address family not supported by protocol) [IP: 2001:648:2000:de::211 80]
Error [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                   
  Unable to connect to security.ubuntu.com:80 (1.0.0.0), end of time
0% [Connect to gr.archive.ubuntu.com (32.1.6.72)] [Connect to security.ub

---

### Post by PmDematagoda on 2007-12-04
Ok, then try changing the location of the servers in Software Sources in System>Administration>Software Sources to one that is close to you as the current one is.

---

### Post by PLIACHAS PASCHALIS on 2007-12-04
i changed to the main server and it says:
failed -  0 B - Release.gpg [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg

---

### Post by zvacet on 2007-12-04
```
sudo aptitude update
```

---

