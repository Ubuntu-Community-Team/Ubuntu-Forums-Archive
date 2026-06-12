---
title: "New to Xubuntu"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Alacard on 2008-01-03
I'm really new a linux, but I finally managed to get xubuntu on my laptop. I tried arch and ubuntu and I kept getting a kernal panic error... read around alittle bit them pull out one of my ram chip and everthing started to run great  finally :). this is my system specs
p4 1.7Ghz
20 gig hard drive...yup only 20
and now 256 ram

I will be putting a new ram chip in soon, but in the mean time is xubuntu my best option for running linux? It came basic no programs are some good one out there for programing and daily use stuff?Last question I promise... when I go into mozilla tools addon "get ubuntu addon" they all tell me not supported (i386)

thanx for the help, just trying to make sure its all set up, before I deploy with the military and have no internet again

---

### Post by skymera on 2008-01-03
my laptop uses xubuntu

1.8 AMD Sempron
50GB HDD
192MB RAM

it runs 'ok'. 7.04 ran much MUCH better.

if your puttin more RAM in perhaps give Gnome a try?

daily use?

perhaps.
-OpenOffice
-Amsn
-Swiftfox/Firefox/Swiftweasel/Icewease (any others?)

dont know preogramming software sorry

---

### Post by taurus on 2008-01-03
Sounds like you don't have any repo available in /etc/apt/sources.list.  Can you open terminal and post the output of this command here?

```
cat /etc/apt/sources.list
```

---

### Post by Alacard on 2008-01-03
I ran it in terminal and got this



## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Alacard on 2008-01-03
this mean I have to verify my securty some how?

---

### Post by taurus on 2008-01-03
Edit /etc/apt/sources.list

```
gksudo mousepad /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```
Now, try to install your app again to see if it goes through.

---

### Post by Alacard on 2008-01-03
thanx for the help its updating and upgrading now... I ran a live ubuntu disc once and there was some cool stuff...was kinda bummed when xubuntu didnt have it. thanx again :). this runs so much better in linux then in windows

---

### Post by Free Penguin on 2008-01-04
If you want here there is a simple (and tested) guide to install aMSN SVN with tcl/tk 8.5 with antialiasing on Ubuntu: [http://www.freepenguin.it/tip8-en.html](http://www.freepenguin.it/tip8-en.html)


Free Penguin

---

