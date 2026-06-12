---
title: "how to install cups?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by szymon_g on 2007-05-19
hi. 
i've got this problem, becouse i've installed from alternate cd :P

this is my repository.list

################################################3
# wziete z [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 

deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse


################################################
# wziete z forum.ubuntu.pl

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

#deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main
#deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main
#deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main

deb [http://www.kadu.net/download/binary/ubuntu/repo](http://www.kadu.net/download/binary/ubuntu/repo) feisty main

deb [http://www.gnugadu.org/packages/ubuntu/](http://www.gnugadu.org/packages/ubuntu/) feisty main


deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free

deb [http://deb.svx.pl](http://deb.svx.pl) feisty main universe
deb-src [http://deb.svx.pl](http://deb.svx.pl) feisty universe

deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) feisty-seveas all

deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) feisty restricted universe multiverse preview

deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse

deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) feisty-cafuego all

deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) feisty-darkmagez all

(i've taken some of them from here

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

and the others are taken from official polish forum

when i type : sudo apt-get install cups
i get this :
szymon@linugrat:~$ sudo apt-get install cups

Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Reading state information... Gotowe
Pakiet cups nie ma dost&#281;pnej wersji, ale odnosi si&#281; do niego inny pakiet.
Zazwyczaj oznacza to, &#380;e pakietu brakuje, zosta&#322; zast&#261;piony przez inny
pakiet lub nie jest dost&#281;pny przy pomocy obecnie ustawionych &#378;róde&#322;.
E: Pakiet cups nie ma kandydata do instalacji
szymon@linugrat:~$ 

any ideas?

---

### Post by scrooge_74 on 2007-05-19
sudo apt-get install cupsys

---

### Post by szymon_g on 2007-05-19
thanx...
shame on me, 'cose i couldn't find an answer :P
i saw that you use Xubuntu. maybe you know answer for my other question :

[http://ubuntuforums.org/showthread.php?t=447977](http://ubuntuforums.org/showthread.php?t=447977)

it's about icons on xfce.

---

