---
title: "Could not download all repository indexes??"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ktoooom on 2007-05-29
hi guys I am having problem with my download manger can any one help me 
Its appear 
Could not download all repository indexes

he repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not resolve ']zajoulnet.com:8080'
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not resolve ']zajoulnet.com:8080'
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:) Could not resolve ']zajoulnet.com:8080'

by the way ']zajoulnet.com:8080' is my ISP

my source list

# 
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

please help my:D

---

### Post by taurus on 2007-05-29
Does this happen recently?  Is your network working at all?

---

### Post by ktoooom on 2007-05-31
yes my network is working 
i can surf the net
i can download & upload 


please guys I need help

any one?

---

### Post by ktoooom on 2007-06-01
please guys need help 

I DO NOT WANT TO GO BACK TO   XP

---

### Post by popie on 2007-06-01
I get the same message (with no URLs listed), but after clicking Close I get another error:

An error occured
E: could not get lock /var/lib/apt/lists/lock - open (11 resource temporarily unavailable)
E: Unable to lock the list directory

ideas?

---

### Post by joe007 on 2007-06-05
Exact same issue.

Tried deselecting all third-party options in the Software Source

testing now


P.M. Dawn anyone... plastic! what!  :)

---

