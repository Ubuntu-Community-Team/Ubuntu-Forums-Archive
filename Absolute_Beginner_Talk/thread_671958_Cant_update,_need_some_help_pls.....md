---
title: "Cant update, need some help pls...."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by limsengwee1988 on 2008-01-19
I cant update my Ubuntu 7.10, whenever i run my update manager, there will be an error msg like this:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

when i try to update in terminal, there is this error msg, need some help here:
aaron@aaron-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg 
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by dustman on 2008-01-19
do you have an internet connection working on your computer? :)

---

### Post by limsengwee1988 on 2008-01-19
yes, i do have an internet connection, and i can browse the internet through firefox oso....

---

### Post by c0met on 2008-01-19
A message like this will happen if the servers are down or if a package has been withdrawn. I'd just leave it and try again a bit later.

---

### Post by limsengwee1988 on 2008-01-19
But i tried many times addy but the problem still occurs, is there a possibility that there is another problem??

---

### Post by c0met on 2008-01-19
It might be that you have a respository listed in [COLOR="Purple"]**System >> Administration >> Software Sources**[/COLOR] (Third Party Software) that is no longer active. You could also try connecting to another server. You'll also find that option in [COLOR="Purple"]**System >> Administration >> Software Sources**[/COLOR]

---

### Post by limsengwee1988 on 2008-01-19
what do i have to do in software sources?? Do i have to tick all the third party software?? How do i connect to another server from software resources???

---

### Post by limsengwee1988 on 2008-01-19
When i want to change any options in the software sources menu, it has this msg coming out:
The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.

Y is there this msg even when i am able to connect to the internet in firefox??

---

### Post by limsengwee1988 on 2008-01-19
Sum1 please help me solve my problem, need to get ubuntu up and running urgently....

---

### Post by c0met on 2008-01-19
in System >> Administration >> Software Sources, you will see text that says "download from" if you click on the button, you can select a server anywhere in the world.

Is Firefox working when you get that network message?

---

### Post by limsengwee1988 on 2008-01-19
yes, firefox is working, but anything that requires updating in ubuntu says that i dun have a working internet, wat is the problem??

---

### Post by limsengwee1988 on 2008-01-19
Be4 this, i couldnt connect even using firefox, but after i read some tutorials in the forum bout changing sumthing from true to false i was able to connect to the internet on firefox but i cannot do any updating... can any1 help me???

---

### Post by dustman on 2008-01-19
you could edit the apt-get sources.list (i find it easier than from synaptic).
To edit:
```
sudo gedit /etc/apt/sources.list
```
The following is my "sources.list":```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ro.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ro.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

#KDE 4.0 REPOSITORY START
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
#KDE 4.0 REPOSITORY END


#AVANT Windows Manager
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

#SCREENLETS
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets

deb http://debian.websterwood.com/ feisty main
deb-src http://debian.websterwood.com/ feisty main
```
I don't have any problems with any of these repositories. You could compare your "sources.list" with mine, and see where the problem might be.

Hope it helps!

Radu

---

### Post by limsengwee1988 on 2008-01-19
I checked my source list and is is like this:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

i copy ur source list and paste it into my source list but the same problem still occur, any other idea to fix the problem...

I think is the problems with the connection settings, because i can browse in firefox but cannot download any updates. Any idea??

---

### Post by limsengwee1988 on 2008-01-19
For your information, previously i wasnt even able to browse the internet in firefox, then after that i saw something in the forum saying about typing about:config in the firefox address bar and disable ipv6, i did that and it allowed me to browse the internet on firefox but i still do not have internet connection on other applications.

---

### Post by limsengwee1988 on 2008-01-19
my problem is solved after doing things mention from this link:
[http://ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

---

### Post by c0met on 2008-01-19
Thank you for the link. I'm glad that you managed to sort it out.

---

