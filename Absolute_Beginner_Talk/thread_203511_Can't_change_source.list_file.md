---
title: "Can't change source.list file"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2006-06-25
When I enter "sudo apt-get install wget",  I get the following..
john@john-desktop:~$ sudo apt-get install wget
E: Type '*:' is not known on line 15 in source list /etc/apt/sources.listE: The list of sources could not be read.
john@john-desktop:~$

Also when I start Synaptic Package Manager,  I get....

E: Type '*:' is not known on line 15 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

What does this noob need to do?:confused:

---

### Post by illynova on 2006-06-25
[QUOTE=johnfarrow]When I enter "sudo apt-get install wget",  I get the following..
john@john-desktop:~$ sudo apt-get install wget
E: Type '*:' is not known on line 15 in source list /etc/apt/sources.listE: The list of sources could not be read.
john@john-desktop:~$

Also when I start Synaptic Package Manager,  I get....

E: Type '*:' is not known on line 15 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

What does this noob need to do?:confused:[/QUOTE]


Can you post your sources.list for us to see? If you're unsure of how to do that, just type in:


```

sudo gedit /etc/apt/sources.list

```


And then post the contents in a reply.

---

### Post by johnfarrow on 2006-06-25
## MAJOR BUG FIX UPDATES produced after the final release

## UBUNTU SECURITY UPDATES

## UNIVERSE AND MULTIVERSE REPOSITORY

## BACKPORTS REPOSITORY

## PLF REPOSITORY

## WINE

## SKYPE
*: deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by digby on 2006-06-25
There should be a lot more to your sources.list, but from that bit, I can tell you that the last line is wrong.  The '*:' probably got copied and pasted from something else because deb [http://.](http://.).. should be the beginning of that line.  So you can remove it (and any other instances thereof), and then try again.  Don't forget that after you  edit souces.list, you have to run```
sudo apt-get update
``` or update via synaptic.

---

### Post by johnfarrow on 2006-06-25
When I remove it, it says I dont have permission to save the file.  How dod I do that?

---

### Post by digby on 2006-06-25
Only the root user has permission to write to sources.list, so to edit it you have to act as root.  You can do this by (in a terminal) typing```
sudo gedit /etc/apt/sources.list
```  it will ask for your password and then let you make changes to the file.

---

### Post by johnfarrow on 2006-06-25
Say,  Thanks a lot.
  It looks like that fixed it.  At least I am not getting that error message now.

You de Man!!!

---

### Post by digby on 2006-06-25
Just glad I could help.  Happy apt-ing

---

### Post by al7anash on 2008-01-13
I have the same problem ... this is my source list > Itried to install java from some sources and I ended up with errors and I can't update my list. This is my list

# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc+ps3 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc+ps3 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy multiverse
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-backports main restricted universe multiverse
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
## Custom archive with a PS3-capable version of hal.

# Line commented out by installer because it failed to verify:
deb deb [http://people.ubuntu.com/~cjwatson/ps3](http://people.ubuntu.com/~cjwatson/ps3) gutsy main
# Line commented out by installer because it failed to verify:
deb-src deb [http://people.ubuntu.com/~cjwatson/ps3](http://people.ubuntu.com/~cjwatson/ps3) gutsy main

deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security main restricted
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security universe
deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) gutsy-security multiverse
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse

I'm using ubuntu in my ps3. please help and thanks

---

