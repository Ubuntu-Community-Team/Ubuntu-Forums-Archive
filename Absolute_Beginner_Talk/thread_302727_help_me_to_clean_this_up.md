---
title: "help me to clean this up"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by verby on 2006-11-19
i was installing driver/program which i don't need anymore. however i have a reminder (beside volume control) that it must be reinstalled but can't find archive for it. I went to synaptic and all my repos are gone, because this message blocks it ... at least i think. how to get rid of this?

---

### Post by jaboua on 2006-11-19
Well, it would be helpful if you could post more details...

But anyway, in many cases this command can be used to sort things out:
```
sudo apt-get install -f
```

---

### Post by verby on 2006-11-19
that's the message i've got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.

---

### Post by PriceChild on 2006-11-19
Could you post the output of ```
cat /etc/apt/sources.list
```please.

---

### Post by verby on 2006-11-20
that's what i'm getting:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by verby on 2006-11-20
help... can't do updates or synaptic or anything. how to clean unfinished dab or corrupted? still have a little icon/reminder beside volume control!!!

---

### Post by PriceChild on 2006-11-20
Have you tried
```
sudo apt-get -f install
```

---

### Post by arnieboy on 2006-11-20
> **verby said:**
> that's the message i've got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.

what does:
```
sudo apt-get update
```
followed by
```
sudo apt-get -f install
```
give?

---

### Post by verby on 2006-11-20
after typing sudo apt-get -f install it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.

i have the .deb package of this on my desktop. tryed double click fie but it says:

"Could not open 'oss-linux_v4.orc2-177_i386.db'
The age might be corrupted or you are not alowed to open the file. Check the permissions of the file."

it is a small file/driver for my sound card 'audiophie 2496'
what should i do next?

---

### Post by arnieboy on 2006-11-20
if its a debian package which I suppose it is (since you are trying to install it with dpkg), rename the file as
oss-linux_v4.orc2-177_i386.deb and copy it as sudo to
/var/cache/apt/archives
and try doing apt-get -f install again.

---

### Post by verby on 2006-11-20
arnieboy...
what is the comand to copy as sudo to /var/cache/apt/archives ...
sorry for basic question... i've been on ubuntu only for a 3 days :)

---

### Post by PriceChild on 2006-11-20
```
sudo cp <<name_of_file>> /var/cache/apt/archives
```
While in the same dir as the file.

---

### Post by verby on 2006-11-20
didn't help...
after sucessful copyin to /var/cache/apt/archives and doing apt-get -f install  i've got:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by PriceChild on 2006-11-20
> **verby said:**
> doing apt-get -f install
It is ```
**sudo** apt-get -f install
```& make sure synaptic etc. aren't open.

---

### Post by verby on 2006-11-20
pricechild:
i've tryed this and:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.

??? i put archive in archive folder already???

---

### Post by verby on 2006-11-20
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.

what do i do now?

---

### Post by verby on 2006-11-21
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report

really stuck... can't install, reinstall or do anything!!!!!
how to clear this out?

---

### Post by PriceChild on 2006-11-21
*bump*

Anyone got any ideas?

---

### Post by arnieboy on 2006-11-21
> **verby said:**
> E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report

really stuck... can't install, reinstall or do anything!!!!!
how to clear this out?
where exactly did you get this deb package from? considering the fact that its your 3rd/4th day on ubuntu, i was just wondering. Please do not take it otherwise. Can you please link us to any howto or list of instructions which you followed?

---

### Post by verby on 2006-11-21
i've got it from [http://www.opensound.com/](http://www.opensound.com/)
its a driver for autiophile 2496 sound card
all i did is double clik on it to install it :(

---

