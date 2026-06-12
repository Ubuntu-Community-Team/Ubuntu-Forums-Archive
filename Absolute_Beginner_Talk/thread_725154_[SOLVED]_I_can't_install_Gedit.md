---
title: "[SOLVED] I can't install Gedit"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by fulgencio on 2008-03-15
Hi, after upgrading I found out my gedit had disappeared. When I try to reinstall it, I get

[PHP]-laptop:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gedit: Depends: libgtksourceview2.0-0 (>= 1.90.4) but it is not going to be installed
         Depends: python-pygtksourceview (>= 2.0.0) but it is not going to be installed
E: Broken packages
[/PHP]

any help?

---

### Post by taurus on 2008-03-15
Do you have all the repos enable in /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by glennric on 2008-03-15
Try doing 
```
sudo apt-get update && sudo apt-get upgrade
```
then try to install gedit.

---

### Post by glennric on 2008-03-15
> **taurus said:**
> Do you have all the repos enable in /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

All of those packages are in gutsy/main (or gutsy-updates/main for newer versions)
Those should be enabled by default.

---

### Post by Cresho on 2008-03-15
it says you have broken packages.  It could be that you either have been cut off from some servers temporarily, or that you need to change your software source under administration and enable download of source files and use the main server instead of the other one.  update the packages like the guy up recommended with the command line but not necessery since it asks you to refresh your lists repo and stuff.  THen try and install it again.

---

### Post by handydan918 on 2008-03-15
When there are broken packages, the package dependencies must be resolved before doing anything else.
Often, this will fix it...```
sudo apt-get install -f
```

If that fails, aptitude sometimes will ride to the rescue...

```
sudo aptitude install <packagename>
```

and then look at the error output and the proposed solutions. If the first proposal fails, try the next one, and so on.

---

### Post by fulgencio on 2008-03-15
so I did:

[PHP]luis@luis-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://hn.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://hn.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ppa.launchpad.net/robster/ubuntu gutsy main
[/PHP]

---

### Post by taurus on 2008-03-15
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  

Now run

```
sudo apt-get update
sudo apt-get install gedit
```

---

### Post by fulgencio on 2008-03-15
Thanks everyone I did:

[PHP]-laptop:~$ sudo aptitude install gedit
[/PHP]

answered YES to everything and it worked, 
best wishes

---

### Post by Cresho on 2008-03-15
:guitar:

---

