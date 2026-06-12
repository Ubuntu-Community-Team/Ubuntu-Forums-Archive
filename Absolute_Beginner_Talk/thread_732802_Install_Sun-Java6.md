---
title: "Install Sun-Java6"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by jfwb on 2008-03-23
I have tried to install sun-java6 with the result below.  I have had no better result with "Add-Remove programs" or "Synaptic Package Manager".  Can anyone please suggest some way forward?

~$ sudo apt-get install sun-java6-jre
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
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-03-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-03-0ubuntu2) but it is not installable
E: Broken packages

---

### Post by kellemes on 2008-03-23
Can you first try the following from terminal please?
```
sudo apt-get -f install
```

---

### Post by bhavi on 2008-03-23
Hello you can try 
```
sudo apt-get update
sudo apt-get -f install 
```

Or you can open up synaptic package manager (Preferences -> Administration -> Synaptic Package Manager)

and click on Edit -> Fix broken packages 

to fix broken packages..

---

### Post by Ub1476 on 2008-03-23
Or maybe:

```
sudo apt-get install ubuntu-desktop --reinstall

sudo apt-get install *java package*
```

---

### Post by jfwb on 2008-03-24
Thanks for those suggestions. I have tried them all but the situation is unchanged.  I tried again to install sun-java6-jre using the synaptic package manager but get told -

Could not mark all packages for installation or upgrade.
The following packages have unresolved delendencies.
Mahe sure that all required repositories are added and enabled in the preferences.
sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
 	ia32-sun-java6-bin (=6-03-0ubuntu2) but it is not installable

Why should these things not be installable?
Any more ideas?

---

### Post by greg_barton on 2008-03-26
I fixed it with the following command:

sudo apt-get autoremove
sudo apt-get install sun-java6-bin

In my case I'd installed a previous version of java (sun-java6-bin 6-04-0ubuntu1 methinks, or whatever's 7.10) and there were some packages left over when another update had removed some of them, but not all of them.  Consequent attempts to install sun-java6-bin would fail.  AFter doing autoremove to get rid of the errant packages all was well.

---

### Post by jfwb on 2008-03-26
Thanks. I tried those two commands and this is the result:

john@john-desktop:~$ sudo apt-get autoremove
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:~$ sudo apt-get install sun-java6-bin
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
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
                 Depends: unixodbc but it is not installable
                 Depends: libstdc++5 but it is not installable
E: Broken packages

I suspect there must be something basically wrong with my set up.  Perhaps I need to try a completely new install?

---

### Post by kellemes on 2008-03-26
I think you better post /etc/apt/sources.list
It seems there is something wrong with your repositories..

---

### Post by jan quark on 2008-03-26
what the...

in the last days there are many questions and problems regarding this java installation

anybody knows something more specific? and updated broken package? a bug?  :confused:

---

### Post by jfwb on 2008-03-27
> **kellemes said:**
> I think you better post /etc/apt/sources.list
It seems there is something wrong with your repositories..

This may be getting a bit beyond me but I think the following is what you are asking for:
Sorry if it is a bit long.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

I think there must be something seriously wrong because mostly when I try to install  something I get a message to the effect that "This application conflicts with other installed software ". [I] am then told to "Switch to the 'synaptic' package manager to resolve this conflict." but that doesn't help.

---

### Post by PmDematagoda on 2008-03-27
Open Software Sources in System>Administration>Software Sources and then select all the options except for the CD-ROM in the Ubuntu Software tab, after that is done try running:-
```
sudo apt-get install -f
```
again.

---

### Post by jfwb on 2008-03-31
> **PmDematagoda said:**
> Open Software Sources in System>Administration>Software Sources and then select all the options except for the CD-ROM in the Ubuntu Software tab, after that is done try running:-
```
sudo apt-get install -f
```
again.
Thanks for the suggestion.  I tried that but the result was exactly the same as my original post.
Can someone tell me how to remove the java installed by Ubuntu so I can try to start from a clean slate. Thanks,

---

### Post by luceerose on 2008-03-31
Open up Synaptic. Have a look at my screenshot down the bottom of my post. Look in the left-hand section of Synaptic in my screenshot and see if you have some of the options I do.

In particular, see the options that say (auto removeable), (residual config) and (local or obsolete) ?

You have already done autoremove from the command line, so that won't be there,
but if there are any packages sitting in the other 2 categories { (residual config), (local or obsolete) }, right-click on them & 'Mark for complete removal'

---

### Post by jfwb on 2008-04-02
Thank you. I found there were auto removable items so I ran autoremove from the command line again and this time it worked.  I then ran sudo apt-get install sun-java6-bin again and that worked right up to the point where I had to accept Sun's conditions.  At this point the OK at the bottom of the screen could not be clicked to indicate acceptance and the whole process was just stalled - no way forward and no way back!
Making progress but by small degrees.  Perhaps I should just try again?

---

### Post by doorknob60 on 2008-04-02
Did you check I accept :P?

---

### Post by zvacet on 2008-04-02
```
sudo apt-get install ubuntu-restricted-extras
```

---

