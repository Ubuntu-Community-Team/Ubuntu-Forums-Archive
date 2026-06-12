---
title: "Install packages error"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by yidaho on 2007-02-20
When tying to Add/remove software I get the following error messages: 

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

and on running apt-get update, i get:

apt-get update
E: Malformed line 4 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)


Any advice on how to fix the problem will be greatly appreciated.

Paul

---

### Post by Shatrat on 2007-02-20
Sounds like there is a typo or something in your /etc/apt/sources.list file at line 4.
Could you post the contents or just put a # in front of line 4?
Youll have to edit as administrator, either 
sudo nano /etc/apt/sources.list 
or 
gksudo gedit /etc/apt/sources.list

---

### Post by taurus on 2007-02-20
Post your /etc/apt/sources.list.d/edgy-universe.list here then.

```
cat /etc/apt/sources.list.d/edgy-universe.list
```

---

### Post by yidaho on 2007-02-20
cat /etc/apt/sources.list.d/edgy-universe.list

# automatically added by gnome-app-install on 2007-02-08 01:20:23.166222
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe #Added by software-properties

---

### Post by yidaho on 2007-02-20
gksudo gedit /etc/apt/sources.list

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

---

### Post by taurus on 2007-02-20
> **yidaho said:**
> cat /etc/apt/sources.list.d/edgy-universe.list

# automatically added by gnome-app-install on 2007-02-08 01:20:23.166222
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates universe #Added by software-properties

Edit your /etc/apt/sources.list.d/edgy-universe.list

```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```
and place a # in front of the line 4 in there.

```
#deb http://security.ubuntu.com/ubuntu edgy-security
```
Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by yidaho on 2007-02-20
Sorted.

Much appreciated any very quick.

Ta

Paul

---

### Post by mango.muncher on 2007-02-26
Hi
Instead of commenting out line 4, you may want to try and correct it.

> gksudo gedit /etc/apt/sources.list.d/edgy-universe.list

remove your # from your line 4 and add the word "universe" which appears to be missing.

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

I had a similar problem , the word "universe" was dropped during an update.

---

### Post by satz13 on 2007-03-16
I had a similar problem post installing IE4linux....I commented all the lines  after running

gksudo gedit /etc/apt/sources.list.d/edgy-universe.list

Then running 

sudo aptitude update

sudo aptitude upgrade

thanks again taurus

---

