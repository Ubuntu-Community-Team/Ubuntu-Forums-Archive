---
title: "synaptic couldn't stat"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by theking2 on 2006-05-01
In the process of adding a soundcard to my ubuntu installation I'm stuck. The Synaptic package manager says:
W: Couldn't stat source package list [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ch.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by renzokuken on 2006-05-01
make sure all the repos are enabled by doing

```
sudo gedit /etc/apt/sources.list
```

and uncomment anything that starts "deb http://...etc" , save it when ur finished

then do 

```
sudo apt-get update
```

and try again

---

### Post by theking2 on 2006-05-01
[QUOTE=renzokuken]make sure all the repos are enabled by doing

```
sudo gedit /etc/apt/sources.list
```

and uncomment anything that starts "deb http://...etc" , save it when ur finished

then do 

```
sudo apt-get update
```

and try again[/QUOTE]

Thanks Renzo, I got reported some additional updates. What is a bit worrying is that sources.list reports some of the hosts containing unsupported packages. Is it save to uncomment them *all*? Or do do I run into sever problems when doing so? To be honest I would assess myself as a "beginner" on Linux.

---

### Post by renzokuken on 2006-05-01
if your only using the ones in the list already i.e. the ones that contain "ubuntu" in the address, then they are pretty safe, the warning is more of a formality, ive never had problems

here is my sources.list as an example for you

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./
## created by arnielistenadded

```

just noticed i havent uncommented the backports, dunno why just forgot

---

### Post by theking2 on 2006-05-01
Thanks Renzo, that did work, no complaints anymore.

I did uncomment the backport one's as I have a pretty old Gateway2000 PPro system with a SB16 Soundcard and an ancient S3/Virge card. These coming of age I thought I just include them.

---

### Post by DooX on 2006-05-01
Hello to all,this is my first post.Im very new to Linux used Gentoo before few months but wasnt ok with me.Now im on Ubuntu.So far ok.
Regarding this story about Synaptec.In my list file isnt every link unccoment but Synaptec is working,but sometimes I also get some errors like that.When i do things from first post everything is great then.Is that maybe because only few of them are uncommented?

---

### Post by renzokuken on 2006-05-01
yes, uncomment them all......some packages have dependencies that require other packages to be installed

---

