---
title: "synaptic doesn't start"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-01-16
I'm having a problem opening synaptic, every time I open it I get this error.

[[IMG]http://img361.imageshack.us/img361/604/screenshot2up4.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshot2up4.png)

How would I go about fixing it?

Also, I have a few additional repositories in my sources.list, is there an easy way to add the keys I need to verify them?

---

### Post by taurus on 2007-01-16
From this from a terminal so see whatever what's the problem is!

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by bapoumba on 2007-01-16
Hello,
in addition, also post the output to cat **/etc/apt/sources.list**.

---

### Post by unabatedshagie on 2007-01-16
Here's my source.list```
# Treviño's Ubuntu Edgy Sources list
# http://download.tuxfamily.org/3v1deb/blog/?page_id=13
#
# Firstly made on source-o-matic (http://www.ubuntulinux.nl/source-o-matic) list
# Added many extra repository
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL --quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE
#


# Ubuntu supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main

# Seveas' packages (GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl edgy-seveas all
deb-src http://mirror.ubuntulinux.nl edgy-seveas all

# kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest edgy main
deb-src http://kubuntu.org/packages/kde-latest edgy main
# deb http://kubuntu.org/packages/kde4-3.80.2 ./

# kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest edgy main
deb-src http://kubuntu.org/packages/koffice-latest edgy main

# kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest edgy main
# deb-src http://kubuntu.org/packages/amarok-latest edgy main
#deb http://kubuntu.org/packages/amarok-144 edgy main

# Bleeding edge wine packages
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main

# The Opera browser (packages) (GPG key: 6A423791)
deb http://deb.opera.com/opera etch non-free

# Google picasa packages
deb http://dl.google.com/linux/deb/ stable non-free

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

# Pouit repository- Ubuntu 6.10 "edgy eft" (GPG key: 12B83718)
deb http://download.tuxfamily.org/pouit edgy extra openalchemist ati-drivers #macbook
deb-src http://download.tuxfamily.org/pouit edgy extra openalchemist ati-drivers #macbook

## archive.kubuntu.de / archive.czessi.net
# The repository from Kubuntu Germany
# GPG key-file: http://archive.czessi.net/ubuntu/kczessi.gpg
# sudo apt-key add kczessi.gpg
deb http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu edgy main restricted universe multiverse preview

# E-Yagi Consulting Community Repository (GPG: 4B6E7209)
deb http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu edgy main restricted universe multiverse

# Ubuntu Taiwan ubuntu extra repository
deb http://apt.ubuntu.org.tw ubtw/
deb http://apt.ubuntu.org.tw ubtw-testing/

# # Achim's Unofficial 'edgy' Kubuntu packages
# deb http://www.mpe.mpg.de/~ach/kubuntu/edgy ./
# deb-src http://www.mpe.mpg.de/~ach/kubuntu/edgy ./

# # Ubuntu edgy University Klagenfurt packages
# # $ wget http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub
# # $ sudo apt-key add uniklu-debuild.pub 
# #   uniklu:         backports and new packages   
# #   uniklu-desktop: packages for uniklu desktop
# #   uniklu-intern:  not freely redistributable (jvm), or modified packages
# #   uniklu-nfsv4:   nfsv4 kernel and packages
# #   uniklu-vserver: vserver kernel
# #   uniklu-testing: packages not ready for general use !
# deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu
# deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-desktop
# deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-intern
# deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-nfsv4
# deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-vserver
# deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-testing
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-desktop
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-intern
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-nfsv4
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-vserver
# deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ edgy uniklu-testing

## SimplyMepis packages (distro based on k-ubuntu)
# deb http://apt.mepis.org/6.0/ mepis main

# Ekiga and Debian pkg-voip
deb http://pkg-voip.buildserver.net/ubuntu edgy main

# superm1's repository (mythtv and other nonfree) (GPG key: 80DF6D58)
deb http://home.eng.iastate.edu/~superm1 edgy all
deb-src http://home.eng.iastate.edu/~superm1 edgy all

# Official Beryl Ubuntu Packages (GPG key: 1609B551)
# GPG key-file: http://ubuntu.beryl-project.org/1609B551.gpg
deb http://ubuntu.beryl-project.org edgy all
deb-src http://ubuntu.beryl-project.org edgy all

# Freedesktop compiz packages
deb http://gandalfn.club.fr/ubuntu/ edgy stable
deb-src http://gandalfn.club.fr/ubuntu/ edgy stable
# deb http://gandalfn.club.fr/ubuntu/ edgy dev git
# deb-src http://gandalfn.club.fr/ubuntu/ edgy dev git

# Subpixel Font rendering packages
# Improved font rendering - May violate some patents
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts main
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts main

# Murrine Ubuntu Repository (GPG key: B54820BC)
# GPG key-file: http://malteo.homelinux.net/B54820BC.gpg
deb http://malteo.homelinux.net edgy-malteo all
deb-src http://malteo.homelinux.net edgy-malteo all

# gandalfn misc packages (anjuta and other devs)
deb http://gandalfn.club.fr/ubuntu/ edgy misc
deb-src http://gandalfn.club.fr/ubuntu/ edgy misc

# Others mlind experimental misc Packages
deb http://www.elisanet.fi/mlind/ubuntu edgy experimental
deb-src http://www.elisanet.fi/mlind/ubuntu edgy experimental

# Skype packages
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Easycam packages
deb http://blognux.free.fr/debian unstable main

# Audacious
deb http://vdlinux.sourceforge.jp/ experimental audacious
deb-src http://vdlinux.sourceforge.jp/ experimental audacious

## Listen
# deb http://theli.free.fr/packages/ dapper listen theli listen-unstable
# deb-src http://theli.free.fr/packages/ dapper listen theli listen-unstable

# Geole's Ubuntu Repository
# GPG key-file: http://www.geole.info/fileadmin/data/misc/geole.info-apt-key.gpg
# sudo apt-key add geole-apt-key.gpg
deb http://ubuntu.geole.info/ edgy universe multiverse

# Linux2Go Ubuntu Packages (GPG key: E8BDA4E3)
deb http://www.linux2go.dk/ubuntu edgy main
deb-src http://www.linux2go.dk/ubuntu edgy main

# GCompris, Televidilo, Kdocker, Frozen-Bubble...
deb http://thomas.pub.enix.org/debian/ edgy main
deb-src http://thomas.pub.enix.org/debian/ edgy main

# Asher256's Repository
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

# Gauvain Repository
deb http://gauvain.tuxfamily.org/repos edgy contrib
deb-src http://gauvain.tuxfamily.org/repos edgy contrib

# Tvfreeplayer Packages
deb http://www.tvfreeplayer.com/linux/ubuntu/dapper/ unstable main

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb http://snapshots.ekiga.net/ubuntu/ edgy main
deb-src http://snapshots.ekiga.net/ubuntu/ edgy main
# deb http://snapshots.voxgratia.org/ubuntu/ edgy main
# deb-src http://snapshots.voxgratia.org/ubuntu/ edgy main

# seb128 repository (gaim - rhythmbox)
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./

## lprod packages: many audio/video apps: avidemux, cinelerra...
# deb http://lprod.org/deb/edgy/ ./
# deb-src http://lprod.org/deb/edgy/ ./

## Mjpegtools and Cinelerra packages (choose your arch)
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
# deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
##deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
##deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
# deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./
##deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
##deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
 
## LiVes dapper package 
# deb http://people.ubuntubrasil.org/~rclbelem/lives/edgy/ ./binary/

## A little too quiet
# deb http://apt.alittletooquiet.net/staging dapper main

## Jahshaka Packages
# deb http://repo.jahshaka.org/ubuntu/dapper binary-i386/

## Spring Packages
# deb ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /
# deb-src ftp://ftp.gwdg.de/pub/linux/people/fbo/debspring/dapper/ /

## debian.wgdd.de Ubuntu Repository (GPG key: E394D996)
# deb http://debian.wgdd.de/ubuntu edgy universe
# deb-src http://debian.wgdd.de/ubuntu edgy universe

## VLC nightlies
# deb http://nightlies.videolan.org/build/edgy-i386 /

# Cafuego's edgy Stuff: Broadcom firmware, google-earth, beagle (GPG key: 969F3F57)...
deb http://au.ubuntu.cafuego.net edgy-cafuego all bcm43xx
deb-src http://au.ubuntu.cafuego.net edgy-cafuego all bcm43xx

# Debuntu Ubuntu edgy packages
# GPG Key: http://repository.debuntu.org/GPG-Key-chantra.txt
deb http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

# BMPx edgy Repository
# GPG key-file: http://files.beep-media-player.org/packages/bmp-packages.pubkey
deb http://files.beep-media-player.org/packages/ubuntu edgy main testing
deb-src http://files.beep-media-player.org/packages/ubuntu edgy main testing

# Morgoth Repository (Monkey's Audio, xmms pugins, vlc plugins, gqview, audacity...)
deb http://morgoth.free.fr/ubuntu edgy-backports main
deb-src http://morgoth.free.fr/ubuntu edgy-backports main

# ATi & nVidia drivers Ubuntu packages
# GPG key: http://albertomilone.com/drivers/tseliot.asc
# deb http://albertomilone.com/drivers/unstable/edgy/32bit binary/
deb http://albertomilone.com/drivers/edgy/nonlegacy/32bit binary/

## Latest Nvidia drivers in restricted modules packages
# deb http://amaranth.selfip.com/ edgy lrm
# deb-src http://amaranth.selfip.com/ edgy lrm

# Givre's repository (ntfs-3g & fuse 2.5.3) - NTFS writing support
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
deb-src http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main

# Automatix (GPG key: 521A9C7C)
deb http://www.getautomatix.com/apt edgy main

# SoS: SeerOfSouls - e17 (Enlightenment DR 17)
# GPG-Key: http://seerofsouls.com/keys/hawkwind.asc
deb http://SeerOfSouls.com/ edgy e17 contrib
deb-src http://SeerOfSouls.com/ edgy contrib e17

# edevelop - e17 (Enlightenment DR 17)
deb http://edevelop.org/pkg-e/ubuntu edgy e17
deb-src http://edevelop.org/pkg-e/ubuntu edgy e17

# XDTV
deb http://nicolas.estre.free.fr/ubuntu dapper main experimental

# Musicbrainz
deb http://users.musicbrainz.org/~luks/ubuntu edgy musicbrainz
deb-src http://users.musicbrainz.org/~luks/ubuntu edgy musicbrainz

# imbrandons software repository (GPG key: 887D9FD2)
deb http://www.imbrandon.com/packages edgy all
deb-src http://www.imbrandon.com/packages edgy all

# Candyz's Ubuntu Packages
# GPG key: http://cle.linux.org.tw/candyz/Ubuntu/candyz.key
deb http://cle.linux.org.tw/candyz/Ubuntu/edgy i386/

# The Ubuntu NLP Repository (GPG key: 8ABD1965)
deb http://cl.naist.jp/~eric-n/ubuntu-nlp edgy nlp english delph-in misc
deb-src http://cl.naist.jp/~eric-n/ubuntu-nlp edgy nlp english delph-in misc

# Ubuntu System Administrator packages
# mirror: http://ubuntu.moshen.de
deb http://ubuntu.systemadministrator.org edgy all
deb-src http://ubuntu.systemadministrator.org edgy all


# Treviño's Ubuntu edgy Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" software: aMule, amsn, mplayer, moto4lin, flashplugin & flashplayer (9.x)...
# Further informations: http://3v1n0.tuxfamily.org
deb http://download.tuxfamily.org/3v1deb edgy 3v1n0
deb-src http://download.tuxfamily.org/3v1deb edgy 3v1n0

# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

## Treviño's Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
## Ubuntu kernels patched with Suspend2 plus other related tools www.suspend2.net
## Warning: they will replace standard ubuntu kernel related packages
# deb http://download.tuxfamily.org/3v1deb edgy suspend2
# deb-src http://download.tuxfamily.org/3v1deb edgy suspend2

#E-UAE and other funky Amiga stuff
deb http://morgoth.free.fr/ubuntu dapper-backports main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main
#AUTOMATIX REPOS END
``` and here's the last part of the output of **sudo apt-get update** ```
Fetched 146kB in 2m9s (1120B/s)                                                
Failed to fetch http://ubuntu.systemadministrator.org/dists/edgy/Release.gpg  Could not resolve 'ubuntu.systemadministrator.org'
Failed to fetch http://ubuntu.systemadministrator.org/dists/edgy/all/i18n/Translation-en_US.bz2  Could not resolve 'ubuntu.systemadministrator.org'
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/Release  Unable to find expected entry  all/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://users.musicbrainz.org/~luks/ubuntu/dists/edgy/musicbrainz/binary-i386/Packages.gz  301 Moved Permanently
Failed to fetch http://users.musicbrainz.org/~luks/ubuntu/dists/edgy/musicbrainz/source/Sources.gz  301 Moved Permanently
Failed to fetch http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.systemadministrator.org/dists/edgy/all/binary-i386/Packages.gz  Could not resolve 'ubuntu.systemadministrator.org'
Failed to fetch http://ubuntu.systemadministrator.org/dists/edgy/all/source/Sources.gz  Could not resolve 'ubuntu.systemadministrator.org'
Reading package lists... Done
W: GPG error: http://pkg-voip.buildserver.net edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: http://snapshots.ekiga.net edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A5E3A5A52ABFCB1
W: GPG error: http://www.linux2go.dk edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A278DF5EE8BDA4E3
W: GPG error: http://download.tuxfamily.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: http://www.elisanet.fi edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: http://gandalfn.club.fr edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: GPG error: http://eyagi.bpa.nu edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0027CEFA4B6E7209
W: GPG error: http://home.eng.iastate.edu edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4C8BC4C880DF6D58
W: GPG error: http://thomas.pub.enix.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F653CB3098D3F7A7
W: GPG error: http://www.imbrandon.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6CFB8719887D9FD2
W: GPG error: http://cl.naist.jp edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B8F0E6C98ABD1965
W: GPG error: http://edevelop.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF
W: GPG error: http://au.ubuntu.cafuego.net edgy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by nonpareilpearl on 2007-01-16
I'm not quite advanced enough an Ubuntu user to offer much in the way of assistance, but I am sorry that you recieved the following error while attempting to use apt-get:
> W: You may want to run apt-get update to correct these problems.

---

### Post by bapoumba on 2007-01-16
Hum ... What an ... extensive sources.list.
Some of the repos are not authenticated, or you did not get the gpg keys (the GPG error). Other ones may be down.
Please comment out all non-official ubuntu repos, and run either **sudo apt-get update** or **sudo aptitude update**.

---

### Post by arnieboy on 2007-01-16
please ignore this post.

---

### Post by arnieboy on 2007-01-16
The broken package came from Trevino's repository. (Please do not use it again)
To fix this try the following (one by one, dont skip steps, and yes steps 2 and 4 are the same but you need to repeat them):
```
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
wget http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo dpkg -i wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
sudo apt-get remove wpasupplicant
sudo apt-get update
```

---

### Post by unabatedshagie on 2007-01-17
> **arnieboy said:**
> The broken package came from Trevino's repository. (Please do not use it again)
To fix this try the following (one by one, dont skip steps, and yes steps 2 and 4 are the same but you need to repeat them):
```
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
wget http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo dpkg -i wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
sudo rm -f /var/lib/dpkg/info/wpasupplicant.postrm
sudo apt-get remove wpasupplicant
sudo apt-get update
```
Thanks, worked a treat.

And don't worry everyone, I have managed to cut down my sources.list a bit :)

---

### Post by haggus on 2007-10-03
thanks for the help I'm not getting to be a linux guru but I am pretty good with searching for answers and subscribing to threads for reference it's a bit uphill but it's better than windows it was actually easier to setup a basic ubuntu on my Athlon 2400 than xp same as kubuntu on my dual core 2.8  I had very little problems other than video drivers. With xp I had driver conflicts and had to search everywhere for drivers for my media readers and onboard sound were not even detected much less my dvb or haupauge card it was far easier to setup ubuntu. Oh well I'm on to other things Like mythtv If I can get that to work I will turf windows for good.

---

