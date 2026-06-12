---
title: "Can not install new software"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2008-03-05
Whenever I try to install a new software i get error. Typical output is: 
[I]

jamil@jamil-desktop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mplayer[/I]

---

### Post by jan quark on 2008-03-05
be sure you have enabled the software sources 

go to

system > administration > software sources

and enble everything except source code and cd

then reload

and try one more time to install

---

### Post by vishzilla on 2008-03-05
Under System-> Admin -> Software Sources, Check all the options except the source code and CD from "**Downloadable from the internet**" and Reload when the dialog box pops up

---

### Post by jamil_1 on 2008-03-05
I have done what i was told to do. but now error is even more weird

[I]jamil@jamil-desktop:~$ sudo apt-get install mplayer
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
  mplayer: Depends: libdvdnav4 (>= 0.1.10) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: libjack0.100.0-0 (>= 0.102.20) but it is not installable
           Depends: liblzo2-2 but it is not installable
           Depends: libopenal0a but it is not installable
           Depends: libsvga1 but it is not installable
E: Broken packages[/I]

---

### Post by hyper_ch on 2008-03-05
post

```

cat /etc/apt/sources.list

```

and what version of ubuntu are you using?

---

### Post by Joeb454 on 2008-03-05
What version of Ubuntu are you using?

:EDIT: Damn beaten to it ;)

---

### Post by jamil_1 on 2008-03-05
I have ubuntu feisty fawn 7.04
out put of  cat /etc/apt/sources.list
  is


jamil@jamil-desktop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-security main restricted

deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-security universe

deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
jamil@jamil-desktop:~$

---

