---
title: "Source List"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-24
hey guys, 
st trying to set up source list and some problem:

vlad@Appoloin:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
vlad@Appoloin:~$ gksudo gedit /etc/apt/sources.list

(gedit:8290): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 
At this point, 
source list open and its empty. when i try to after pasting 

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
i
next it ask to save as per instruction. but fail..
help please

---

### Post by briguy on 2006-05-24
Perhaps instead of doing the gksudo gedit, do a sudo nano.  It may be a gnome issue, and nano is text-based (you could also use vi or emacs, I just find nano really simple and easy).

---

### Post by edwardzafra on 2006-05-24
Shoul my source list be empty at the first place?

---

### Post by user1397 on 2006-05-24
[quote=edwardzafra]Shoul my source list be empty at the first place?[/quote]
i dont think gksudo is meant for the terminal.  (its used in the run application)  Instead just use sudo gedit or sudo nano

---

