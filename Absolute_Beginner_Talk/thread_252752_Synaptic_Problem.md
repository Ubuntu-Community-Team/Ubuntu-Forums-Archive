---
title: "Synaptic Problem"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Anthrax-1039 on 2006-09-07
Righr when i tried to install the repository for "sudo apt-get install build-essential" i mangaed to mess it up. Ive somehow caused my package manager to blow nd not do anything
i cant find how to remover this repository and was wondering if there was anyway to return it to normal.
Also whilst im here i need to get acess to that directory and am not getting anywhere im just co confused.

---

### Post by tatimmer on 2006-09-07
Whe I had problems I resort to the command line.  Edit your /etc/apt/sources.list with the following and then run "sudo apt-get update".  After doing this Synaptic should behave, or just get used to using the commandline.



## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

***************************************************

some misc apt-get commands:
<apt-cache search notsureofpackagename> 
<apt-get update> sources list
<apt-get install packagename>
<apt-get remove packagename>
<apt-get upgrade> all installed packages
<apt-get dist-upgrade>
<dpkg -l *package-name-pattern*> List installed packages matching pattern
<apt-cache showpkg packagename> list package info
<dpkg -S filename>  Which installed package owns the file?
<dpkg -L package> List files in the package
<apt-get autoclean> Run periodically to clean out .deb archives

---

