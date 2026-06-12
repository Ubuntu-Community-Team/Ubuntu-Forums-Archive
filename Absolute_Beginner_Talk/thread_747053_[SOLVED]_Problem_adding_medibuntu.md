---
title: "[SOLVED] Problem adding medibuntu"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by mr wilson on 2008-04-06
I only recently installed ubuntu and tried to add the medibuntu repository. Nothing happened  when I put in the appropriate sudo wget command into the terminal and now I can't do anything - not even update (or sudo apt-get update). When I try to update using update manager, I get the following message:

An unresolvable problem occurred while initializing the package information. 

Please report this bug against the 'update manager' package and include the following error message:

'E:Type '--16:08:03--' is not know on line 1 in sources list /etc/apt/sources.list.d/medibuntu.list, E: The list of sources could not be read'

Please Help:confused:

(Also, how do you report bugs)

---

### Post by seshomaru samma on 2008-04-06
you post bugs [here]("https://bugs.launchpad.net/")
but i think your problem can be solved by editing the sources.list files (the files which contains the sources from which the apt utility installs software)
please post the content of the file , by issuing this command
```
cat /etc/apt/sources.list
```

---

### Post by mr wilson on 2008-04-06
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by seshomaru samma on 2008-04-06
sorry i was wrong, didn't realise midibuntu has its own file , i gusee the file we are looking for is:
```
cat   /etc/apt/sources.list.d/medibuntu.list
```

mine is :
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
#deb-src http://packages.medibuntu.org/ gutsy free non-free
```
yours is probably different

---

### Post by mr wilson on 2008-04-06
Yeah mine did something fairly different - seemed to download something:

```
--16:08:03--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `gutsy.list.1'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

    0K                                                       100%    5.18 MB/s

16:08:05 (5.18 MB/s) - `gutsy.list.1' saved [223/223]
```

---

### Post by seshomaru samma on 2008-04-06
First run the wget command again and see if that solves anything
next try to add midibuntu from synaptic 
if all these don't work
change your medibuntu.list to mine
by issuing the command :
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by FuturePilot on 2008-04-06
It looks like somehow the output of wget got put into the medibuntu.list.
After editing the file with the above instructions run
```
sudo apt-get update
```
to update apt's database

---

### Post by mr wilson on 2008-04-07
Running the wget command didn't achieve anything, neither did trying synaptic (as I couldn't even open it). I changed medibuntu.list to the same as yours and that did the trick. Thanks alot mate. 

 Cheers.

---

