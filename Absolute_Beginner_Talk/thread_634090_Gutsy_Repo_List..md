---
title: "Gutsy Repo List."
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-07
A List found here:. 

[http://graymalkin.wordpress.com/2007/09/25/gutsy-repository/](http://graymalkin.wordpress.com/2007/09/25/gutsy-repository/)

im noy using these, yet. will do when i reinstall.
i posted if some of you missed the Trevino repository for feisty.

Not all of them have GPG keys which you can add manually.

```

#Repository List based on standard gutsy with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg –keyserver subkeys.pgp.net –recv KEY
# gpg –export –armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget URL –quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
#
# In the repository list page there’s also a script that can do this
# work automatically, this is suggested only if you know what you’re doing

# Ubuntu supported packages (GPG key: 437D05B5)
deb http://it.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties
deb http://it.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties
deb http://it.archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://it.archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe #Added by software-properties

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://it.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
deb http://it.archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse
deb http://it.archive.ubuntu.com/ubuntu/ gutsy-security universe multiverse
deb http://it.archive.ubuntu.com/ubuntu/ gutsy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://mi.mirror.garr.it/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://mi.mirror.garr.it/ubuntu gutsy-backports main restricted universe multiverse

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)
deb http://archive.canonical.com/ubuntu gutsy-commercial main

# UbuntuStudio Repository (GPG key: B6A4EB33)
# GPG key-file: http://archive.ubuntustudio.org/ubuntustudio.gpg
deb http://archive.ubuntustudio.org/ubuntustudio gutsy main
deb-src http://archive.ubuntustudio.org/ubuntustudio gutsy main

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-357 gutsy main
deb-src http://kubuntu.org/packages/kde-357 gutsy main
deb http://kubuntu.org/packages/kde-latest gutsy main
deb-src http://kubuntu.org/packages/kde-latest gutsy main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest gutsy main
deb-src http://kubuntu.org/packages/koffice-latest gutsy main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest gutsy main
deb-src http://kubuntu.org/packages/amarok-latest gutsy main

# kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde4-3.90.1 gutsy main
deb-src http://kubuntu.org/packages/kde4-3.90.1 gutsy main

# Bleeding edge wine packages (GPG key: 387EE263)
# GPG key-file: http://wine.budgetdedicated.com/apt/387EE263.gpg
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main

# Seveas’ packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl gutsy-seveas all
deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

# The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

# Google picasa packages (GPG key: 7FAC5991)
deb http://dl.google.com/linux/deb/ stable non-free

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ gutsy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ gutsy free non-free

# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
deb http://archive.czessi.net/ubuntu gutsy main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu gutsy main restricted universe multiverse preview

# Achim’s Unofficial ‘gutsy’ Kubuntu packages
# GPG key-file: http://www.mpe.mpg.de/~ach/ach-gpg.asc
deb http://www.mpe.mpg.de/~ach/kubuntu/gutsy ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/gutsy ./

# Ubuntu gutsy University Klagenfurt packages
# GPG key-file: http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# $ sudo apt-key add uniklu-debuild.pub
# uniklu: backports and new packages
# uniklu-intern: not freely redistributable (jvm), or modified packages
# uniklu-testing: packages not ready for general use
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ gutsy uniklu
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ gutsy uniklu-intern
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ gutsy uniklu-testing
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ gutsy uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ gutsy uniklu-intern
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ gutsy uniklu-testing

# MEPIS improvements, overrides and updates (distro based on kubuntu)
# deb http://apt.mepis.org/mepis32-6.5/ mepis main
# deb http://apt.mepis.org/simply32-6.0/ mepis main

# Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu gutsy main

# MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 gutsy all
deb-src http://home.eng.iastate.edu/~superm1 gutsy all

# Official Beryl Ubuntu Packages (GPG key: 1609B551)
# GPG key-file: http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
deb http://ubuntu.beryl-project.org gutsy main
deb-src http://ubuntu.beryl-project.org gutsy main

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
deb-src http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu gutsy fonts main
deb-src http://www.telemail.fi/mlind/ubuntu gutsy fonts main

## Others mlind experimental misc Packages (GPG key: 937215FF)
## GPG key-file: http://www.telemail.fi/mlind/ubuntu/937215FF.gpg
deb http://www.telemail.fi/mlind/ubuntu gutsy experimental
deb-src http://www.telemail.fi/mlind/ubuntu gutsy experimental

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Geole’s Ubuntu Repository
# GPG key-file: http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
deb http://ubuntu.geole.info/ gutsy universe multiverse
deb-src http://ubuntu.geole.info/ gutsy universe multiverse
deb http://ubuntu.geole.info/ gutsy-backports main universe multiverse restricted
deb-src http://ubuntu.geole.info/ gutsy-backports main universe multiverse restricted

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu gutsy main
deb-src http://www.linux2go.dk/ubuntu gutsy main

# Asher256’s Repository
deb http://asher256-repository.tuxfamily.org gutsy main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Tvfreeplayer Packages (GPG key: )
# GPG key-file: http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg
deb http://www.tvfreeplayer.com/linux/falcon gutsy all
deb-src http://www.tvfreeplayer.com/linux/falcon gutsy all

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ gutsy main
deb-src http://snapshots.ekiga.net/ubuntu/ gutsy main

## lprod packages: many audio/video apps: avidemux, cinelerra…
deb http://lprod.org/deb/gutsy/ ./
deb-src http://lprod.org/deb/gutsy/ ./

# Cinelerra Feisty packages
deb http://www.kiberpipa.org/~gandalf/ubuntu/gutsy/cinelerra/i686/ ./

## Spring Packages (RTS game)
deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/gutsy/ /
deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/gutsy/ /

# Cafuego’s gutsy Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)…
deb http://au.ubuntu.cafuego.net gutsy-cafuego all
deb-src http://au.ubuntu.cafuego.net gutsy-cafuego all

# Debuntu Ubuntu gutsy packages
# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb http://repository.debuntu.org/ gutsy multiverse
deb-src http://repository.debuntu.org/ gutsy multiverse

## BMPx gutsy Repository
## GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
deb http://files.beep-media-player.org/packages/ubuntu gutsy main testing
deb-src http://files.beep-media-player.org/packages/ubuntu gutsy main testing

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey’s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity…
# GPG key-file: http://morgoth.free.fr/files/morgoth-signkey.gpg.asc
deb http://morgoth.free.fr/ubuntu gutsy-backports main
deb-src http://morgoth.free.fr/ubuntu gutsy-backports main

## ATi & nVidia drivers Ubuntu packages
## GPG key: http://albertomilone.com/drivers/tseliot.asc
deb http://www.albertomilone.com/drivers/gutsy/latest/32bit binary/

# Automatix repository (GPG key: E23C5FC3)
deb http://www.getautomatix.com/apt gutsy main

# edevelop - e17 (Enlightenment DR 17)
# GPG key: http://lut1n.ifrance.com/repo_key.asc
deb http://edevelop.org/pkg-e/ubuntu gutsy e17
deb-src http://edevelop.org/pkg-e/ubuntu gutsy e17
deb http://e17.dunnewind.net/ubuntu gutsy e17
deb-src http://e17.dunnewind.net/ubuntu gutsy e17

# Musicbrainz Repository
# GPG key-file: http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu gutsy musicbrainz
deb-src http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu gutsy musicbrainz

## Imbrandons software repository (GPG key: 887D9FD2)
## GPG key-file: http://www.imbrandon.com/packages/887D9FD2.gpg
deb http://www.imbrandon.com/packages gutsy all
deb-src http://www.imbrandon.com/packages gutsy all

## Candyz’s Ubuntu Packages
## GPG key-file: http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
deb http://cle.linux.org.tw/candyz/Ubuntu/gutsy i386/

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg
deb http://cl.naist.jp/~eric-n/ubuntu-nlp gutsy all
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp gutsy all

# Ubuntu System Administrator packages (GPG key: 2F306651)
# GPG key-file: http://ubuntu.moshen.de/2F306651.gpg
deb http://ubuntu.moshen.de gutsy multimedia misc
deb-src http://ubuntu.moshen.de gutsy multimedia misc

## Michael Biebl Tracker Repository (GPG key: BD058554)
## GPG Key-file: http://www.teco.edu/~biebl/biebl.asc
deb http://debs.michaelbiebl.de/ gutsy main
deb-src http://debs.michaelbiebl.de/ gutsy main

# The Consciousness Repository (GPG key: DD385D79)
# GPG key-file: http://debs.peadrop.com/DD385D79.gpg
deb http://debs.peadrop.com gutsy all
deb-src http://debs.peadrop.com gutsy all

## Tolero Ubuntu Repository
deb http://ubuntu.tolero.org/ gutsy main
deb-src http://ubuntu.tolero.org/ gutsy main

# IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
# GPG key-file: http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg
deb http://dl.ivtvdriver.org/ubuntu gutsy all
deb-src http://dl.ivtvdriver.org/ubuntu gutsy all

# syzygy42 repository: avant-window-navigator, exaile, closure… (GPG key: 8434D43A)
# GPG key-file: http://download.tuxfamily.org/syzygy42/8434D43A.gpg
deb http://download.tuxfamily.org/syzygy42/ gutsy all
deb-src http://download.tuxfamily.org/syzygy42/ gutsy all

## Firefox 3.0 alpha builds for gutsy (unstable)
deb http://gnomefreak.youmortals.com/mozilla-testing gutsy main
deb-src http://gnomefreak.youmortals.com/mozilla-testing gutsy main

## Swiftfox (enhanced Firefox for linux) packages
deb http://getswiftfox.com/builds/debian unstable non-free

# Sonnes repository (aMule AdunanZa, Audacious)
deb http://adurepo.altervista.org/ubuntu gutsy all
deb-src http://adurepo.altervista.org/ubuntu gutsy all

# darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
# GPG key-file: http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg
deb http://mirror.randumb.org/darkmagez/repo gutsy-darkmagez multimedia-experimental #core-experimental
deb-src http://mirror.randumb.org/darkmagez/repo gutsy-darkmagez multimedia-experimental #core-experimental

## Raof Repository: newer versions of Compiz, beagle, mono, scribus… (GPG key: 2F306651)
## GPG key-file: http://raof.dyndns.org/falcon/2F306651.gpg
##deb http://raof.dyndns.org/falcon gutsy all
deb-src http://raof.dyndns.org/falcon gutsy all

# FoLKeN ‘Repozytorium’ (GPG key: 6FB65A0F)
deb http://deb.svx.pl/ gutsy main universe bleeding
deb-src http://deb.svx.pl/ gutsy main universe bleeding

# Le dépomaniak repository (GPG key: 1D59E694)
# GPG key-file: http://ubuntu.davromaniak.eu/1D59E694.gpg
deb http://ubuntu.davromaniak.eu gutsy-depomaniak all
deb-src http://ubuntu.davromaniak.eu gutsy-depomaniak all

# Mez’s Repository (GPG key: 6AAAA569)
# GPG key-file: http://apt.sourceguru.net/6AAAA569.gpg
deb http://apt.sourceguru.net gutsy all
deb-src http://apt.sourceguru.net gutsy all

# Ryan Kavanagh’s packages (GPG key: 02544D0E)
# GPG key-file: http://packages.ryanak.ca/02544D0E.gpg
deb http://packages.ryanak.ca ryan-gutsy all
deb-src http://packages.ryanak.ca ryan-gutsy all

# OpenedHand Debian/Ubuntu Packages
deb http://debian.o-hand.com gutsy/
deb-src http://debian.o-hand.com gutsy/

# OpenSync svn ubuntu repository (GPG key: B029CB84)
deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ gutsy main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ gutsy main

# Iuculano’s debian packages (GPG key: AE3BE9AA)
# GPG key-file: http://ubuntu.iuculano.it/AE3BE9AA.gpg
deb http://ubuntu.iuculano.it gutsy amsn thunderbird #ck-kernel #all
deb-src http://ubuntu.iuculano.it gutsy amsn thunderbird #ck-kernel #all

# Elisa Debian Packages
deb http://elisa.fluendo.com/packages gutsy main

# PollyCooke, il repository :)
deb http://download.tuxfamily.org/pollyrepo gutsy/

# Treviño’s Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
# Many “random” bleeding edge software: aMule, aMSN, Mercury, flash…
# Further informations and complete packages list: http://3v1n0.tuxfamily.org
deb http://download.tuxfamily.org/3v1deb gutsy 3v1n0
deb-src http://download.tuxfamily.org/3v1deb gutsy 3v1n0

# Treviño’s Ubuntu gutsy EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…
deb http://download.tuxfamily.org/3v1deb gutsy eyecandy
deb-src http://download.tuxfamily.org/3v1deb gutsy eyecandy

## Treviño’s Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
## Ubuntu kernels patched with Suspend2 plus other related tools www.suspend2.net
## Warning: they will replace standard ubuntu kernel related packages
deb http://download.tuxfamily.org/3v1deb gutsy suspend2
deb-src http://download.tuxfamily.org/3v1deb gutsy suspend2

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt gutsy main

deb http://it.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb http://www.virtualbox.org/debian gutsy non-free
deb http://debian.space-based.de/debs/ experimental main
deb-src http://debian.space-based.de/debs/ experimental main
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://ubuntu.iuculano.it gutsy all
deb-src http://ubuntu.iuculano.it gutsy all
deb http://exodus.xmms.se/debian stable main
deb http://wicd.longren.org gutsy all
#Zonagames repository for Ubuntu linux
deb http://www.zonagames.it/ubuntu/ gutsy main

```

---

### Post by wersdaluv on 2007-12-09
Thanks! :)

---

### Post by PhrankDaChickenGeek on 2007-12-27
Just a note - the CANONICAL COMMERCIAL REPOSITORY isn't

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

it's actually
```

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

```

---

### Post by skymera on 2007-12-27
ok

---

### Post by Perfect Storm on 2007-12-27
o_O
With so many unofficial sources - It will properly go wrong sooner or later.

---

### Post by skymera on 2007-12-27
well, im not using.

just postd if anyone wanted it :)

---

### Post by Biggy on 2007-12-27
# Google picasa packages (GPG key: 7FAC5991)
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

How to input GPG key ????

help.

---

### Post by SOULRiDER on 2007-12-27
Back when dapper was the new version and when edgy came out i liked to use
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by dasunst3r on 2007-12-27
The only unofficial repository I have is Medibuntu.  Can anybody tell me what's special about each of the repositories listed?

---

### Post by flamelab on 2007-12-27
The only thing that someone can do with ALL of these repos is to totally ruin his system .

You only add a repo if you want to install a specific program .

It is highly possible that some of these repos have a duplicate program and , thus , Ubuntu gets confused and apt doesn't know which version to download .

---

### Post by skymera on 2007-12-28
my friend has used these repos before and his systrem was fine.

---

### Post by cmost on 2007-12-29
> **flamelab said:**
> The only thing that someone can do with ALL of these repos is to totally ruin his system .

You only add a repo if you want to install a specific program .

It is highly possible that some of these repos have a duplicate program and , thus , Ubuntu gets confused and apt doesn't know which version to download .

Umm, no.  Apt won't get "confused".  It always tries to upgrade to the newest version unless you've specified otherwise in your preferences file.

---

### Post by hyper_ch on 2007-12-29
> **dasunst3r said:**
> The only unofficial repository I have is Medibuntu.
I tend to think of Medibuntu meanwhile as semi-official. The Howto for medibuntu is actualy in the ubuntu wiki.

> **SOULRiDER said:**
> Back when dapper was the new version and when edgy came out i liked to use
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
Source-o-matic is also available for gutsy. Very handy tool.

---

### Post by jnylen on 2008-01-04
> **cmost said:**
> Umm, no.  Apt won't get "confused".  It always tries to upgrade to the newest version unless you've specified otherwise in your preferences file.
Like others have said, using a bunch of extra repositories is probably a bad idea.  I used 3v1n0's list back when I used Feisty, and I encountered several problems with dependencies.  The more repositories you have, the more likely it is that one of them will try to provide a package which conflicts with an official Ubuntu package.

Now, I only add a third-party repository when I'm certain that I will need to install the software it provides.

---

