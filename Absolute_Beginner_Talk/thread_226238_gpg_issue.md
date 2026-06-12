---
title: "gpg issue"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by drtvasudevan on 2006-07-31
ubuntu with kde desktop and gnome desktop envir
kernal 686

issues with update
synaptic fails to get the gpg files.(perhaps) therefore unable to update.
how to rectify?
:confused: 
tv

---

### Post by Dr. Nick on 2006-07-31
gpg errors shouldnt stop a update, what server does it say doesnt have the gpg key? Most sites have instructions how to add them

---

### Post by drtvasudevan on 2006-07-31
so is this still a network problem?
here is the error msg:
tv

[http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg:](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg:) Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out

---

### Post by Dr. Nick on 2006-07-31
yeah that is a net problem, not sure why though. I just used the repos.

that problem you post will stop upgrades, may post your /etc/apt/sources.list file up, or look at it for errors.

---

### Post by Dr. Nick on 2006-07-31
Ill post mine if you want to comapre
```

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by drtvasudevan on 2006-07-31
> **Dr. Nick said:**
> yeah that is a net problem, not sure why though. I just used the repos.

that problem you post will stop upgrades, may post your /etc/apt/sources.list file up, or look at it for errors.

here it is:
# 


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe
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


# Line commented out by installer because it failed to verify:
#tvdeb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#tvdeb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#tvdeb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#tvdeb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Release i386 (20060601)]/ dapper main restricted
#next from forum
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by Dr. Nick on 2006-07-31
well, yours looks sorta messed us, the lines commented out due to installer parts

you can make a whole new one here

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by drtvasudevan on 2006-08-01
> **Dr. Nick said:**
> well, yours looks sorta messed us, the lines commented out due to installer parts

you can make a whole new one here

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

thank you.
concentrated on the network issue and got it resolved.:p 
the commented out stuff came as i was experimenting.
i got the updates and so i can delete the commented out stuff.:cool: 

the only problem is i have to reset network settings everytime  i boot.
how to make it stick?
:confused:

---

