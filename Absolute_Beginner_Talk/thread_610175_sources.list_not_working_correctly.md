---
title: "sources.list not working correctly"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-11-11
I am currently running gutsy and I am trying to install realplay and adobe reader but I noticed I have a lot of entires in my sources.list that say

# Line commented out by installer because it failed to verify:

When I uncomment them like universe and multiverse I can't seem to find realplay or adobe in synaptic?

---

### Post by Sef on 2007-11-11
Could you post your sources list here, please?  What are your computer specs?

---

### Post by cjnkns on 2007-11-11
Here is sources list
I am just using a DELL Inspiron 9300 is that what you mean by specs?

```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
 deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
 deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
 deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
 deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
 deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
 deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
 deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu gutsy partner
 deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
 deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
 deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
 deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
 deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator


```

---

### Post by cjnkns on 2007-11-12
No body else here had a similar problem?  :confused:

---

### Post by erfahren on 2007-11-12
that happened to me.  I didn't have internet connected while installing Gutsy. 

I basically redid mine manually going by the wiki:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

I actually re-installed Gutsy and remembered to set up my internet with the the desktop CD first and didn't get that mess. (It would be nice if it was automatically corrected after getting the updates the first time and it was able to connect.)

In any event, this is what mine looks like now (I'm using the US mirror) Try it:
```

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted #Added by software-properties

## START -- MANUALLY ADDED
##
## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-free

```

---

### Post by erfahren on 2007-11-12
after posting my sources.list I went and searched Synaptic for realplayer and it didn't come up. I've seen elsewhere that it isn't in the repositories at all.

It seems that this guy was able to find it. See his sources.list (he's in Finland maybe): [http://users.piuha.net/martti/comp/ubuntu/en/install.html](http://users.piuha.net/martti/comp/ubuntu/en/install.html)

Anyway, the thread here is about realplayer in Gutsy: [http://ubuntuforums.org/showthread.php?t=587953](http://ubuntuforums.org/showthread.php?t=587953)

I found acroread, I think its in Medibuntu.

---

### Post by cjnkns on 2007-11-12
Thanks I'll give it a shot

---

