---
title: "i think im having a graphics card problem, random reboot."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by James27 on 2008-02-13
hey guys, looking for a little help but i have had no luck. a finger in the right direction, or a little help would be greatly appreciated
i know that my ps is good, my ram, mobo, etc is good
i suspect im having a graphics card issue, a random reboot happens whenever graphics "intensify¨, i havint installed my nvidea drivers (8400 gs i believe) and have no idea how to . HELP!?!?!?!?!
thanks so much in advance, james.

---

### Post by taurus on 2008-02-13
Look in System -> Administration -> Restricted Drivers Manager and see if your nvidia graphic card is on the list.  If it is, then click enable to install a driver for it.

---

### Post by James27 on 2008-02-13
when i do this i get the following error

You need to install the package

  linux-restricted-modules-2.6.22-14-server

for this program to work.

how do i install this package?

---

### Post by taurus on 2008-02-13
Open the Search option in synaptic and search for it, linux-restricted-modules-2.6.22-14-server.

---

### Post by crjackson on 2008-02-13
> **James27 said:**
> when i do this i get the following error

You need to install the package

  linux-restricted-modules-2.6.22-14-server

for this program to work.

how do i install this package?

```
 sudo apt-get install linux-restricted-modules-2.6.22-14-server
```

---

### Post by James27 on 2008-02-13
let me elaborate on this
i tryed to install the package
i run into the following problems

```
james@james:~$ sudo apt-get install linux-restricted-modules-2.6.22-14-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.22-14-server
james@james:~$ 

```

Can sombody help me understand why this isnt working??

---

### Post by crjackson on 2008-02-13
You need to enable all the repositories I'm guessing.

System>Administration>Software Sources

Then enable them...

---

### Post by James27 on 2008-02-13
im sorry, im not trying to have you hold my hand, but im not seeing what i should be enabling.  somthing in third party? authentication?
thanks in advance again
james

---

### Post by taurus on 2008-02-13
Open a terminal and post the output of this command here.

```
cat /etc/apt/sources.list
```

---

### Post by James27 on 2008-02-13
the output is

```
james@james:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
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
deb http://ubuntu.beryl-project.org edgy main
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
james@james:~$ 

```

---

### Post by Sinkingships7 on 2008-02-13
system -> administration -> software sources.
click the tab that says "third party software" and check the two boxes. when you close, it will ask you to reload the repositories. accept. now use that code.


EDIT: was replying when the post two-up was posted. sorry.

---

### Post by James27 on 2008-02-13
same thing
i have 
archive.canocial.com/ubuntu gutsy partner
archive.canocial.com/ubuntu gutsy partner (source code)
ubuntu.beryl-project.org edgy main
packages.medibuntu.org/ gutsy free non-fee
packages.medibuntu.org/ gutsy free non-fee (source code)

all checked
i went to my command terminal and gave the command 
```
sudo apt-get install linux-restricted-modules-2.6.22-14-server

```

the following happened
```
james@james:~$ sudo apt-get install linux-restricted-modules-2.6.22-14-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.22-14-server

```

again. did i enable a repo i wasnt suposed to? i added the beryl one to my sources a few days ago, but i doubt that this is the cause
thanks
james

---

### Post by James27 on 2008-02-13
anyone?

---

### Post by Sinkingships7 on 2008-02-13
go to system -> administration -> synaptic package manager.

click search, and type (or copy and paste) this without the quotes: "linux-restricted-modules".

look a few down the list that comes up and check the box that says "linux-restricted-modules" (press 'mark for installation') and press apply at the top,

---

