---
title: "apt source list"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by dvdljns on 2006-04-17
some of the programs I need or not on ubuntu. I have read a couple webpages on the subject and still have not been able to setup apt to download from the deb mirrors. can someone post an apt source.lst so I can see what I am doing wrong.](*,)

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=dvdljns]some of the programs I need or not on ubuntu. I have read a couple webpages on the subject and still have not been able to setup apt to download from the deb mirrors. can someone post an apt source.lst so I can see what I am doing wrong.](*,)[/QUOTE]

Here's my sources.list:

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arnielistenadded



You can find your sources.list by doing this in terminal:

> sudo gedit /etc/apt/sources.list

---

### Post by dvdljns on 2006-04-18
thanks for the help but I still get the same error
could not stat source list. Anybody know whats wrong.

---

### Post by pixel80r on 2006-04-20
make sure you do:
sudo apt-get update

after you add new sources to your list.

---

### Post by PriceChild on 2006-04-20
It's probably best to use the following link to generate your own sources list, instead of using someone elses, which could be slow because of different countries :)

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by mjm115 on 2006-04-20
> It's probably best to use the following link to generate your own sources list, instead of using someone elses, which could be slow because of different countries :)

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)


That's what I did

[QUOTE=mjm115]
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

[/QUOTE]

---

### Post by dvdljns on 2006-04-20
I did update than did upgrade.
pricechild I am using debian sources not ubuntu. I removed gnome and replaced it with kde now I want to build my own source Archive? mirror? of debian pckgs. Then I will start rebuilding this distro to be what I want. I still got a lot to learn but my next task is to learn how create a ext2fs on my third partion and rsync all the debian pckgs from the latest stable deb build. I also need to make a 1gig swap. Then install jwm to replace kde. Strip everything off that I can leaving a smaller system to use as a base. Then install only what I need. Then build my own install cd from it.I have 10 comps here waiting be built 8 linux systems want dedicate to certain tasks. 1 win2k and one to conect them all together. but first learn learn learn. so thanks for the help.

---

