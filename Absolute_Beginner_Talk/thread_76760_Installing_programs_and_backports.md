---
title: "Installing programs and backports"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by Philz on 2005-10-15
Hi, I just installed the new version of Kubuntu breezer. I tried to install e.g. nvu, but it said it wasnt listet there, is it because I need some backport?
Thanks in advance for a newbie question :)

---

### Post by aysiu on 2005-10-15
According to [this search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=nvu&sourceid=mozilla-search), it's in Universe. Follow these instructions to get it: [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by Philz on 2005-10-15
Sorry for this newbie question, but what do you mean with, its in universe?

---

### Post by aysiu on 2005-10-15
[QUOTE=Philz]Sorry for this newbie question, but what do you mean with, its in universe?[/QUOTE] Universe is a separate set of repositories. To enable these, you follow the directions in the link I gave you. If you don't know what repositories are, maybe you should read [this](http://www.psychocats.net/essays/linuxguide.php).

---

### Post by Philz on 2005-10-16
Hi, thanks for the links. The reason why I dint substituded the rep. with the ones you gave me, is that I use some Swedish rep. which I would like to continue. Mine are as followed :
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
"/etc/apt/sources.list" 40L, 2090C                            1,1           Top


Do I then just need some backports?'

---

### Post by Philz on 2005-10-16
Okay I tried it anyway, but when I try to install e.g. gaim I get the following error :

e_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package emacs

---

### Post by Philz on 2005-10-16
I forgot to make an update, stupid me :)

---

