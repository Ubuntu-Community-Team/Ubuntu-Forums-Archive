---
title: "Flash Plugin???"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-09-17
HI,What do i need to activate to get flash plugin to appear in synaptic:confused:     (Im useing Kubuntu)

---

### Post by foolsh on 2006-09-17
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

follow this guide it will tell everthing you want to know about everything you want to know and more

but since your using kubuntu like me first install gedit and when says use something like "gksudo apt-get install foobar"
just use sudo or kdesu cause gksudo is native to gnome "ubuntu" only

---

### Post by That Guy X on 2006-09-17
I was on there and it says i need to enable universe and multiverse but when i click on the section for kubuntu it says page not added yet#-o  Can you tell me how?

---

### Post by foolsh on 2006-09-17
```

sudo apt-get install gedit
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
then replace *everything* with
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```
and save 
then
```
sudo apt-get update
```
then run synaptic and do your search

---

### Post by Najand on 2006-09-17
If you cannot add universe and multiverse by clicking, try to do it manually...
Use Console or terminal and run:
```

kdesu kwrite /etc/apt/sources.list

```
then erase # signes before lines starting with "deb" or "deb-src" or "deb cdrom"; then save it and run this command:
```

sudo aptitude update && sudo aptitude upgrade

```

---

### Post by foolsh on 2006-09-17
i find kwrite crashes when envoked with sudo
so i use gedit

---

### Post by Najand on 2006-09-17
Use "kdesu" instead of using "sudo" with KDE applications.

---

