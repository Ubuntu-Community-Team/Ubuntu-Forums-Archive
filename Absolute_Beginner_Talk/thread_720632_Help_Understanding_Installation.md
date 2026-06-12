---
title: "Help Understanding Installation"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by DaddyUnit on 2008-03-10
I'm a brand new Ubuntu/Linux user and have no idea what I'm doing. I'm trying to install CVS. I've read the Ubuntu documentation page and tried to read about synaptic but it's "forbidden". 

I tried using the package installer thing (Applications > Add/Remove) which I think is supposed to find applications, but it doesn't seem to be able to find any CVS server applications.

I've been to the CVS site, downloaded 9M of installation files and found a lovely procedure at [https://help.ubuntu.com/7.04/server/C/cvs-server.html](https://help.ubuntu.com/7.04/server/C/cvs-server.html).

Step 1 of the procedure is "Type sudo apt-get install cvs at a terminal prompt"

I tried this and I get the following response:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package cvs

I couldn't figure out how to change directories in the terminal, but I did find a file manager application (somewhere, I can't find it now) and tried moving my downloaded CVS files to the directory where the terminal prompt seemed to be, but it still can't find the package.

Obviously I don't understand how to install software on Ubuntu and I can't seem to find any procedures for installing CVS on Ubuntu that seem to work. If someone can nudge me in the right direction I'd really appreciate it.

---

### Post by SunnyRabbiera on 2008-03-10
try synaptic, it is more advanced then add/remove.
you will find it in system> administration> synaptic package manager
but there might be the chance you might need to compile something from source, but lets take it by the steps.

---

### Post by Cypher on 2008-03-10
From the terminal please type the following and send us the output
```

cat /etc/apt/sources.list
sudo apt-get update

```

---

### Post by Duck2006 on 2008-03-10
I may be wrong but you have to run

sudo atp-get upgrade
sudo apt-get update

first.

---

### Post by SunnyRabbiera on 2008-03-10
yes but lets take our friend here by the steps, he/she might need more repos and such

---

### Post by DaddyUnit on 2008-03-10
Wow, thanks for the quick response everyone!

Here's the result of the sources.list

vaoig@vaoig-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by SunnyRabbiera on 2008-03-10
alright, give apt get update a shot then see if anything new pops up in synaptic.

---

### Post by forrestcupp on 2008-03-10
> **SunnyRabbiera said:**
> yes but lets take our friend here by the steps, he/she might need more repos and such

This is correct.

Open up Synaptic and go to Settings->Repositories.  In the window that comes up in the 'Ubuntu Software' tab, make sure all of the boxes are checked.  Then exit out of that and click the Reload button.  Then you should be able to do a search for cvs and it will be there ready to install.  You just needed to enable your Universe and Multiverse repositories.

---

### Post by DaddyUnit on 2008-03-10
thanks again...

vaoig@vaoig-desktop:~$ sudo apt-get upgrade
[sudo] password for vaoig:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vaoig@vaoig-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
vaoig@vaoig-desktop:~$ 
vaoig@vaoig-desktop:~$ sudo apt-get install cvs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cvs
vaoig@vaoig-desktop:~$

---

### Post by SunnyRabbiera on 2008-03-10
then it might be something you need to compile then

---

### Post by Shazaam on 2008-03-10
Cvs is in the repo's. Follow forestcupps's advice to enable the other repositories.

---

### Post by DaddyUnit on 2008-03-10
Wow,

I followed forrestcupp's suggestion and installed CVS in minutes!

Thanks to everyone for your help. Hopefully I did the official "thanks" properly and you all get some "thank you" credits or whatever. This is the friendliest, most helpful forum I've ever been to...thanks very much!

---

### Post by oldos2er on 2008-03-10
Just FYI, you might want to read [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

