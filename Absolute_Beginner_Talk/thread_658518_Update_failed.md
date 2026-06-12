---
title: "Update failed"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by cypherzero on 2008-01-04
After a fresh install of Kubuntu Gusty I ran Adept Updater (when I finally got it working). During the download the network disconnected. Now when I run the updater it tells me there is nothing to update, which obviously isn't the case.

More so, when I try to install anything new halfway through it tells me that the update will break dependencies and quits, which is very annoying!

I've tried: restarting the computer and using apt-get update, neither of which work.

Anyone any ideas...?
Thanks.

---

### Post by eternicode on 2008-01-04
You probably have corrupted package file downloads in apt's cache. At a command line, try:

```

$ sudo apt-get clean
$ sudo apt-get autoclean
$ sudo apt-get remove

and

$ sudo apt-get autoremove

```

The "apt-get clean" line should clean out the offending files, the others are for good measure.  After this, try updating again; if adept still gives you issues, try

```
$ sudo aptitude dist-upgrade
```

---

### Post by cypherzero on 2008-01-04
thanks, I tried all of the above, but even the latter dist-upgrade says there is nothing to be updated. I guess I could just wait and see if any upgrades at all appear over the next few days.

---

### Post by eternicode on 2008-01-04
Was adept still giving you grief about dependencies being broken?

---

### Post by RomeReactor on 2008-01-04
Hi. Please open Konsole and run:
```
sudo apt-get update
```
and post any error messages it shows there.

---

### Post by cypherzero on 2008-01-05
No error messages just no updates:

```

**sudo apt-get update**
Get: 1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/main Translation-en_GB
Get: 2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://archive.ubuntu.com gutsy/main Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_GB
Hit http://security.ubuntu.com gutsy-security Release
Hit http://archive.ubuntu.com gutsy/restricted Translation-en_GB
Hit http://archive.ubuntu.com gutsy/multiverse Translation-en_GB
Hit http://archive.ubuntu.com gutsy/universe Translation-en_GB
Get: 3 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_GB
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_GB
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Fetched 3B in 0s (8B/s)
Reading package lists... Done
**sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by ~LoKe on 2008-01-05
Then, simply, there are no updates. ;)

---

### Post by RomeReactor on 2008-01-05
Are you still unable to install anything? please post your source.list:
```
cat /etc/apt/sources.list
```

Also try:
```
sudo apt-get install -f
```
or if that doesn't help:
```
sudo dpkg --configure -a
```

---

### Post by cypherzero on 2008-01-06
> **~LoKe said:**
> Then, simply, there are no updates. ;)
This may be the case, I just find it strange that such a huge download (>100Mb of updates) should fail and next time I start Adept no updates at all appear.

I can install new software though. I previously got a message about broken dependencies but I cant remember what that was.

```

**cat /etc/apt/sources.list**
# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu/ gutsy partner
# deb-src http://archive.canonical.com/ubuntu/ gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu/ gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu/ gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu/ gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
# deb-src http://security.ubuntu.com/ubuntu/ gutsy-security multiverse

```

---

### Post by PmDematagoda on 2008-01-06
Open your sources.list file for editing by executing:-
```
gksudo gedit /etc/apt/sources.list
```
then uncomment the repositories by removing the # in front of them so that lines such as these:-
```
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
```
look like this:-
```
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
```
after the editing is done, save the file and then execute:-
```
sudo apt-get update
```
that should fix your problem.

---

