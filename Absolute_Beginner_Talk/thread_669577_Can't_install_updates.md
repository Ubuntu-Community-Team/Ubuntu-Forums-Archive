---
title: "Can't install updates?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by blazini on 2008-01-16
When I click on the "install updates" button, I get the error message "Could not apply changes! Fix broken packages first". It doesn't download or install anything. How do I know what packages are broken and what to fix?

---

### Post by FuturePilot on 2008-01-16
Try this in a terminal first
```
sudo apt-get install -f
```
That should fix any broken packages.

---

### Post by blazini on 2008-01-16
I just tried that, it removed 7 packages but it still didn't fix the updates even after a restart.

---

### Post by FuturePilot on 2008-01-16
Try the Mark All Upgrades button in Synaptic and see what happens. It might be that something needs to be removed and the Update Manager cannot handle removal of packages. Also in Synaptic try Edit>Fix Broken Packages.

---

### Post by blazini on 2008-01-16
Keep hitting a dead end. I hit "Mark all upgrades" and the "apply" button doesn't become active, so I assume nothing was marked. Same thing with fix broken packages. 
I appreciate your help.

---

### Post by blazini on 2008-01-17
anybody?

---

### Post by plucky on 2008-01-17
blazini,

Open Synaptic package manager and click on **Custom Filters** > **Broken** to see what Synaptic thinks is broken.

Have you tried ```
sudo dpkg --configure -a
``` as yet?

Please copy and paste output ```
cat /etc/apt/sources.list
```

---

### Post by blazini on 2008-01-17
> **plucky said:**
> blazini,

Open Synaptic package manager and click on **Custom Filters** > **Broken** to see what Synaptic thinks is broken.

Have you tried ```
sudo dpkg --configure -a
``` as yet?

Please copy and paste output ```
cat /etc/apt/sources.list
```Just tried the broken filters in synaptic, I didn't see anything.

Tried the sudo dpkg --configure -a, not sure what it does but it didn't fix anything.

Now when I upgraded to gutsy from fiesty, I had a problem finding gutsy repos. I found a post on here with a bunch of repos and used it as my sources.list not sure if it caused any problems. I removed the sources from system/administration/software sources, but they still remain in /etc/apt/sources.list, so here is the output 

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
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-updates universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-security universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)

# UbuntuStudio Repository (GPG key: B6A4EB33)
# GPG key-file: [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg)

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)

# kubuntu.org packages for KDE4 alpha-1 (GPG key: DD4D5088)

# Bleeding edge wine packages (GPG key: 387EE263)
# GPG key-file: [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)

# Seveas’ packages (GPG key: 1135D466)
# GPG key-file: [http://mirror.ubuntulinux.nl/1135D466.gpg](http://mirror.ubuntulinux.nl/1135D466.gpg)

# The Opera browser (packages) (GPG key: 6A423791)

# Google picasa packages (GPG key: 7FAC5991)

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)

# The repository from Kubuntu Germany
# GPG key-file: [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)

# Achim’s Unofficial ‘gutsy’ Kubuntu packages
# GPG key-file: [http://www.mpe.mpg.de/~ach/ach-gpg.asc](http://www.mpe.mpg.de/~ach/ach-gpg.asc)

# Ubuntu gutsy University Klagenfurt packages
# GPG key-file: [http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub](http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub)
# $ sudo apt-key add uniklu-debuild.pub
# uniklu: backports and new packages
# uniklu-intern: not freely redistributable (jvm), or modified packages
# uniklu-testing: packages not ready for general use

# MEPIS improvements, overrides and updates (distro based on kubuntu)

# Ekiga and Debian pkg-voip

# MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)

# Official Beryl Ubuntu Packages (GPG key: 1609B551)
# GPG key-file: [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)

# Ubuntu repository for Screenlets (GPG key: F854AFD7)
# GPG key-file: [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg)

# Subpixel Font rendering packages (GPG key: 937215FF)
# Improved fonts on LCDs - WARNING: May violate some patents
# GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)

## Others mlind experimental misc Packages (GPG key: 937215FF)
## GPG key-file: [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg)

# Skype packages

# Geole’s Ubuntu Repository
# GPG key-file: [http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg](http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg)

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)

# Asher256’s Repository

# Tvfreeplayer Packages (GPG key: )
# GPG key-file: [http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg](http://www.tvfreeplayer.com/linux/falcon/tvfreeplayer.gpg)

# gnomemeeting - ekiga (GPG key: 52ABFCB1)

## lprod packages: many audio/video apps: avidemux, cinelerra…

# Cinelerra Feisty packages

## Spring Packages (RTS game)

# Cafuego’s gutsy Stuff: Broadcom firmware, google-earth, secondlife (GPG key: 969F3F57)…

# Debuntu Ubuntu gutsy packages
# GPG Key: [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)

## BMPx gutsy Repository
## GPG key-file: [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey’s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity…
# GPG key-file: [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc)

## ATi & nVidia drivers Ubuntu packages
## GPG key: [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)

# Automatix repository (GPG key: E23C5FC3)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

# edevelop - e17 (Enlightenment DR 17)
# GPG key: [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)

# Musicbrainz Repository
# GPG key-file: [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/public.key)

## Imbrandons software repository (GPG key: 887D9FD2)
## GPG key-file: [http://www.imbrandon.com/packages/887D9FD2.gpg](http://www.imbrandon.com/packages/887D9FD2.gpg)

## Candyz’s Ubuntu Packages
## GPG key-file: [http://cle.linux.org.tw/candyz/Ubuntu/candyz.key](http://cle.linux.org.tw/candyz/Ubuntu/candyz.key)

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: [http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg](http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg)

# Ubuntu System Administrator packages (GPG key: 2F306651)
# GPG key-file: [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg)

## Michael Biebl Tracker Repository (GPG key: BD058554)
## GPG Key-file: [http://www.teco.edu/~biebl/biebl.asc](http://www.teco.edu/~biebl/biebl.asc)

# The Consciousness Repository (GPG key: DD385D79)
# GPG key-file: [http://debs.peadrop.com/DD385D79.gpg](http://debs.peadrop.com/DD385D79.gpg)

## Tolero Ubuntu Repository

# IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
# GPG key-file: [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg)

# syzygy42 repository: avant-window-navigator, exaile, closure… (GPG key: 8434D43A)
# GPG key-file: [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)

## Firefox 3.0 alpha builds for gutsy (unstable)

## Swiftfox (enhanced Firefox for linux) packages
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

# Sonnes repository (aMule AdunanZa, Audacious)

# darkmagez repository: rhythmbox and newer gtk (GPG key: A3012FB3)
# GPG key-file: [http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg](http://mirror.randumb.org/darkmagez/repo/A3012FB3.gpg)

## Raof Repository: newer versions of Compiz, beagle, mono, scribus… (GPG key: 2F306651)
## GPG key-file: [http://raof.dyndns.org/falcon/2F306651.gpg](http://raof.dyndns.org/falcon/2F306651.gpg)
##deb [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) gutsy all

# FoLKeN ‘Repozytorium’ (GPG key: 6FB65A0F)

# Le dépomaniak repository (GPG key: 1D59E694)
# GPG key-file: [http://ubuntu.davromaniak.eu/1D59E694.gpg](http://ubuntu.davromaniak.eu/1D59E694.gpg)

# Mez’s Repository (GPG key: 6AAAA569)
# GPG key-file: [http://apt.sourceguru.net/6AAAA569.gpg](http://apt.sourceguru.net/6AAAA569.gpg)

# Ryan Kavanagh’s packages (GPG key: 02544D0E)
# GPG key-file: [http://packages.ryanak.ca/02544D0E.gpg](http://packages.ryanak.ca/02544D0E.gpg)

# OpenedHand Debian/Ubuntu Packages

# OpenSync svn ubuntu repository (GPG key: B029CB84)

# Iuculano’s debian packages (GPG key: AE3BE9AA)
# GPG key-file: [http://ubuntu.iuculano.it/AE3BE9AA.gpg](http://ubuntu.iuculano.it/AE3BE9AA.gpg)

# Elisa Debian Packages

# PollyCooke, il repository :)

# Treviño’s Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
# Many “random” bleeding edge software: aMule, aMSN, Mercury, flash…
# Further informations and complete packages list: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
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
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

could this be the problem?

---

### Post by plucky on 2008-01-18
blazini,

According to your sources list you have the **Italian** and **US** repositories enabled.I would recommend regenerating your sources list from [here](http://www.ubuntu-nl.org/source-o-matic/) and then try ```
sudo apt-get update
sudo apt-get upgrade
```
> Tried the sudo dpkg --configure -a, not sure what it does but it didn't fix anything.
To find out what a command does, open a terminal window and type ```
man commandname
```

Good luck

---

