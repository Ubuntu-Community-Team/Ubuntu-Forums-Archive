---
title: "[SOLVED] synaptic not downloading"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-10-08
My Synaptic Package Manager has stopped downloading!!!! I've checked that my internet connection is working (firefox and email).
I had a problem a short while ago trying to install a wireless usb adapter (freezes the computer).
I gave up on that and removed the driver folder (ie. usr/src/rt73....) 
Any ideas??

---

### Post by cameronw on 2007-10-08
Could you have accidentally removed the repos you are downloading from and not reloaded the repo list?   3rd party repo or is it an official Ubuntu one?

---

### Post by Dr Small on 2007-10-08
Please post the output of this command:
```
cat /etc/apt/sources.list
```

Dr Small

---

### Post by axamax on 2007-10-08
It was a third party driver for the wireless. I was just going to install Kcontrol and it wouldn't download.
I tried to reload Synaptic but that wouldn't download either.

---

### Post by axamax on 2007-10-08
ubuntu@ubuntu-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
ubuntu@ubuntu-desktop:~$

---

### Post by cameronw on 2007-10-08
Hmmm. Try installing something from Terminal  sudo apt-get install (package to install) and check for any error messages.

---

### Post by axamax on 2007-10-08
ubuntu@ubuntu-desktop:~$ sudo apt-get install kcontrol
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdebase-data kicker libkonq4
Suggested packages:
  khelpcenter kicker-applets menu
The following NEW packages will be installed
  kcontrol kdebase-data kicker libkonq4
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.9MB of archives.
After unpacking 33.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libkonq4 kdebase-data kicker kcontrol
Install these packages without verification [y/N]? y
0% [Connecting to gb.archive.ubuntu.com (198.18.1.9)]
ubuntu@ubuntu-desktop:~$ 



Wouldn't connect!!

---

### Post by cameronw on 2007-10-08
Well i'm baffled. Sorry can't help there.

---

### Post by axamax on 2007-10-08
Anyone else??

Is there anything similar to system restore on Ubuntu? Can I do a repair installation so I don't upset my settings?

---

### Post by cameronw on 2007-10-08
Maybe try sudo apt-get update to update package lists.

---

### Post by axamax on 2007-10-08
ubuntu@ubuntu-desktop:~$ sudo apt-get update
Password:
0% [Connecting to gb.archive.ubuntu.com (198.18.1.9)] [Connecting to security.ubuntu.com (198.18.1.8)]

Still not downloading but seemed to get one stage further
 ie Connecting to security

Is reinstalling the only way out of this??

---

### Post by axamax on 2007-10-09
Appears to be a problem with the UK server. I've just changed the setting in software sources to Main server instead of United Kingdom server. Synaptic works. Changed it back and it didn't. So I've left it on Main server now


Thanks for trying guys.

---

### Post by greenstar on 2007-10-09
[Please mark your thread solved.]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") You'll find it in the "Thread Tools" menu. 

Greenstar

---

