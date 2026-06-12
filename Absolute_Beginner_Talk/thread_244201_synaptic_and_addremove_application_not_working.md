---
title: "synaptic and add/remove application not working"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by yasasvy on 2006-08-26
Hi!
i have recently shifted from windows to ubuntu.. (abt a week ago). not the prob is that ... i tried to install wine application using APT repository,
. then after adding the channel.. i got the error message saying that

E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 35 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

.. ive tried the apt-get update and and apt-get install -f commands.. but the prob is persisting .. 

now this is how my souce file looks like

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted

plz help me with this . iam really desparate :?

---

### Post by deadgobby on 2006-08-26
That is very simple. Here edit the wine line with this

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

You are just missing "deb http:// "

Gobby

---

### Post by yasasvy on 2006-08-26
thnx !! a lot .. that  did the trick.. actually i had a prob editing the sources file ... jus now i found how to do that.. starting to get the zest of it .. 
thnx again!!

---

### Post by deadgobby on 2006-08-26
That is great that you found how to edit the sources.list and glad to be of help. I use wine here and there. There is alot of usful info for Ubie on the net. It was very helpful that you posted your sources list too. That gave good details on what may be causing the problem. 
 Gobby \\:D/

---

