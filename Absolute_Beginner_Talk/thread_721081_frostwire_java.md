---
title: "frostwire java"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by skylinedna on 2008-03-11
When i try install java or iced tea i get this
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
  icedtea-java7-jre: Depends: java-common but it is not installable
 
how to i install java common  also to install sunjava6 i need something like unixodbc   how do i get that

---

### Post by blasteryui on 2008-03-11
> **skylinedna said:**
> When i try install java or iced tea i get this
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
  icedtea-java7-jre: Depends: java-common but it is not installable
 
how to i install java common  also to install sunjava6 i need something like unixodbc   how do i get that

Wait do you want Sunjava6? If so then...
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin java -version
```
then do this..
```
java -version
```
it should look something like this..
> mbl:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
if it doesn't then do this...
```
sudo update-alternatives --config java
```
and set Java 1.6 as your default, then do the check Java version code and make sure it looks like mine, it it looks like mine then you got Java 1.6
I hope that helps.
Blasteryui

---

### Post by skylinedna on 2008-03-11
Hey tried that came up with this
There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure.

i tried installing sunjava from terminal using sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-fonts

fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not installable
                 Depends: libstdc++5 but it is not installable
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
E: Broken packages

cant do it through add remove programs cause it says it need same dependencied and synaptic wont work either. id rather do it through terminal anyway. 

and im trying to install sun java6 yes

---

### Post by skylinedna on 2008-03-12
anyone?? i gone through java guides on forums and cant find soloution

---

### Post by GSF1200S on 2008-03-12
Ok.. lets try to straighten this out..

sudo apt-get -f install

sudo dpkg --configure -a

Please post the contents of:

sudo gedit /etc/apt/sources.list

---

### Post by skylinedna on 2008-03-12
in terminal skylinedna@MISKNK:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfaad2-0 libxvidcore4 libmp4v2-0 libx264-54 libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
skylinedna@MISKNK:~$ sudo dpkg --configure -a
skylinedna@MISKNK:~$ sudo gedit /etc/apt/sources.list


then a text doc come up.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by GSF1200S on 2008-03-12
Ahaa! Run:

sudo gedit /etc/apt/sources.list

again. Uncomment (take the # out from front of) all lines that have deb in it. Ill include mine so you can see what I mean.. It looks like the installer commented them out- maybe you didnt have an internet connection when you installed?

After you uncomment everything, open a terminal and do:

sudo apt-get update

and then if youre willing:

sudo apt-get upgrade

Then try to fix java as mentioned above.

Good luck! ;)

---

### Post by GSF1200S on 2008-03-12
Ehh... sorry. Forgot to include my sources.list. Here it is:

> 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted 

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted  

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted  

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe  
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe  

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse  
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse  

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse  
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse  

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) gutsy partner  
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) gutsy partner  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse  
# deb [http://packages.dfreer.org/](http://packages.dfreer.org/) gutsy main
deb [http://ppa.launchpad.net/daniel-rocher/ubuntu](http://ppa.launchpad.net/daniel-rocher/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/daniel-rocher/ubuntu](http://ppa.launchpad.net/daniel-rocher/ubuntu) gutsy main

# deb cdrom:[Buntu Repo DVD 6]/ gutsy main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 6]/ gutsy-backports main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 6]/ gutsy-security main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 6]/ gutsy-updates main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 5]/ gutsy main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 5]/ gutsy-backports main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 5]/ gutsy-security main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 5]/ gutsy-updates main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 4]/ gutsy main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 4]/ gutsy-backports main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 4]/ gutsy-security main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 4]/ gutsy-updates main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 3]/ gutsy main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 3]/ gutsy-backports main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 3]/ gutsy-security main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 3]/ gutsy-updates main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 2]/ gutsy main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 2]/ gutsy-backports main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 2]/ gutsy-security main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 2]/ gutsy-updates main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 1]/ gutsy main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 1]/ gutsy-backports main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 1]/ gutsy-security main multiverse restricted universe  
# deb cdrom:[Buntu Repo DVD 1]/ gutsy-updates main multiverse restricted universe  








Youll notice the ones that are commented are my DVD repo cd's. All the others do not have a # in front of them.

---

