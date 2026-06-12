---
title: "Update-manager won't update"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Bradwin on 2008-02-27
I'm quite a beginner with Linux.

I decided to try Xubuntu on my EEE-PC, but I can't see any updates listed in the Update Manager.
If I press "Check", it asks me for the admin password, I enter it, he quickly download like 5 files or something "Reading ..." but no updates appear in the list.

The strange thing is, I installed Xubuntu in VMWare as well, and if I go to the Update Manager over there, I see over 40 updates listed.

I modified my /etc/apt/sources.list:
I commented the CDROM lines, only the two archive.canonical.com ones are not commented.

The PC is connect to the internet, I can surf the web.

What am I missing?

---

### Post by taurus on 2008-02-27
Close down the update manager window and see what happens when you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bradwin on 2008-02-27
Update:
```
eee@eee-laptop:/$ sudo apt-get update
[sudo] password for eee:
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Hit http://archive.canonical.com gutsy Release
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 1B in 0s (3B/s)
Reading package lists... Done
eee@eee-laptop:/$ 
```
Upgrade:
```
eee@eee-laptop:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eee@eee-laptop:/$ 
```

Does not look like much is moving?

This is the /etc/apt/sources.list by the way:
```
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```


It looks like there is no official Ubuntu download site in the list, atleast not uncommented.
which one should i enable, all?

---

### Post by taurus on 2008-02-27
You hardly have any repo enable in /etc/apt/sources.list.  Therefore, you need to edit /etc/apt/sources.list to enable all the repos in there.

```
gksudo gedit /etc/apt/sources.list
```
Remove the # in front of all the lines that start with **deb** & **deb-src** except the first one, cdrom.  You want to leave the first line comment out.  Save it and close down gedit window.  

Now, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by philinux on 2008-02-27
You need to know that a # means a comment only so your sources aren't active. you prbably installed without being connected to the net.

Use Sytem>Admin>Software sources list. Ive got the top 4 ticked.

---

### Post by sayakb on 2008-02-27
@OP

For a GUI based method, goto System -> Administration -> Software Sources
Tick all the checkboxes under the Ubuntu software and Updates tabs.

---

### Post by Bradwin on 2008-02-27
It all works now, It's all so obvious that I feel a bit ashamed. thx for pointing me the right place.

---

