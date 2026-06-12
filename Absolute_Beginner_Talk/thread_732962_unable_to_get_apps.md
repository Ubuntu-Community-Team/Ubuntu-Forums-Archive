---
title: "unable to get apps"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by hellomoto on 2008-03-23
Trying to download applications with "add/remove programs" keeps returing errors for any program i try download.


```
The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working Internet connection. 
```

then i click on refresh to try and update the information, it downloads a small file but still won't install the program.

If i try and select a program i get this message:

```

Canonical Ltd. provides technical support and security updates for Potato Guy
Pidgin cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.
```


thanks for any help!

---

### Post by (((X))) on 2008-03-23
Sources list has never been downloaded.
Open synaptic, on panel goto settings>sources and checkmark everything WEO cd-rom.

---

### Post by hellomoto on 2008-03-23
Do you mean download package information? I start to..... a window comes up stating its downloading package information but it makes no progress.  I have checked every box for it to download in software sources WEO cd rom.

```
Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

I could not see the option "sources"  in synaptic package manager, I looked under the settings tab.

---

### Post by jan quark on 2008-03-23
please select all sources in 
system > administration > software sources
except cd

post also the output of this command

```
cat /etc/apt/sources.list
```

does this help?
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by hellomoto on 2008-03-23
hey 

cat /etc/apt/sources.list result:

```
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

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
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

here is result for sudo apt-get update:

```

Err http://security.ubuntu.com gutsy-security Release.gpg                                                                   
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com gutsy Release.gpg                                                                             
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com gutsy Release.gpg                                              
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun


```

here is result for sudo apt-get upgrade:

```

mark@mark-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

all check boxes are ticked in software sources WEO Cd-ROM

--- I think this maybe a connection issue. But I am surfing on firefox fine.

---

### Post by hellomoto on 2008-03-23
is this any help

---

### Post by forrestcupp on 2008-03-23
Open up Synaptic and go to Settings->Repositories.  That's another way to get to software sources.  You said you already checked all of the boxes, but you need to find the 'Download from' drop down box.  Try setting it to a different server than what you are using.  Then close out that window and hit the Reload button in Synaptic.  If it doesn't give any errors, try to install something from Synaptic.

---

