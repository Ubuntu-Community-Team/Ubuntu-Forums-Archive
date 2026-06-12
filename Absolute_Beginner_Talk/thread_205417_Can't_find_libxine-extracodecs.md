---
title: "Can't find libxine-extracodecs"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by sternael on 2006-06-28
As the title suggests, I can't find the package libxine-extracodecs using Synaptic (or using apt-get). I think that I have enabled multiverse and pressed the reload button but it just does not work. Please help me (this makes me go crazy)!

---

### Post by johnc4510 on 2006-06-28
That package is in the multiverse repository. Please post this file:
sudo gedit /etc/apt/sources.list
Copy and Paste that in a terminal
Terminal in Gnome:
Applications>Accessories>Terminal

---

### Post by sternael on 2006-06-28
Sorry, that was foolish of me not posting it... =) 


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by johnc4510 on 2006-06-28
Add these two lines at the bottom and retry:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
NOTE: Be sure to save the file after adding the two lines

---

### Post by sternael on 2006-06-28
Thanks, it worked fine. Why did Synaptic fail...

---

### Post by Jagot on 2006-06-28
[QUOTE=sternael]Thanks, it worked fine. Why did Synaptic fail...[/QUOTE]

The sources from which both Synaptic and apt/aptitude obtain software are set out by what is in your sources.list file.  Your sources.list did not oriiginally allow access to the multiverse repository so Synaptic/apt could not obtain files from it.

---

