---
title: "where can get the package xserver-xorg-video-openchrome?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by gagatz on 2007-12-11
Hello, where do i get the package 
xserver-xorg-video-openchrome
? 
It is not listed in synaptic, although all repositories are switched on???

---

### Post by meborc on 2007-12-11
that is wierd, as i can find it in the repos```
kaspar@obpos:~$ apt-cache search xserver-xorg-video-openchrome
xserver-xorg-video-openchrome - X.Org X server -- VIA display driver

```
can you post your sources.list```
cat /etc/apt/sources.list
```

did you do ```
sudo apt-get update
```after enabling all repositories?

EDIT: are you still using breezy? :o

---

### Post by gagatz on 2007-12-11
Hello, doing this
apt-cache search xserver-xorg-video-openchrome 
doesn't yield any results

I'm currently using the dapper 6.06

and my sources.list is:



## sources.list
## General comments about the sources.list file
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 
## Comment about the 'Update' repositories
## Comments about the role of the updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 
## Comment on the 'Universe' repositories
## Comment about the support limitations of Universe & Multiverse
## repositories as well as licence restrictions and update policies.
## Please satisfy yourself as to your rights to use the software.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

## Comment on the 'Backports' repository
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Comment about update and security update limitations
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

---

### Post by meborc on 2007-12-11
i don't think thi package is in dapper repositories... you can check here [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/) (under the x-window section)

i think you might want to upgrade to a newer version of ubuntu

EDIT: this pack does not exist in any other stable versions then gutsy, so if you want it, you should upgrade

---

