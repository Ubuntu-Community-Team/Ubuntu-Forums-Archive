---
title: "Duplicate sources"
date: 2012-03-28
forum: Catalan Team
---

### Post by jinglada on 2012-03-28
Benvolgudes i benvolguts,

L'actualització de programari em dona el següent error:

W: Duplicate sources.list entry [http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu/](http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_lucid_main_binary-amd64_Packages)

i a l'/etc/apt/sources.list hi ha això:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://ad.archive.ubuntu.com/ubuntu/](http://ad.archive.ubuntu.com/ubuntu/) lucid-security multiverse

# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
# deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main # disabled on upgrade to jaunty
# deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main # disabled on upgrade to jaunty

##Kdenlive 0.7.4
# deb [http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu) karmic main # desactivat en actualitzar a karmic
##deb-src [http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu](http://ppa.launchpad.net/dominik-stadler/ppa/ubuntu) jaunty main

# Firefox 3.5
# deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main # desactivat en actualitzar a karmic

#Jaunty [9.04]
# deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main # desactivat en actualitzar a karmic
# deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main # desactivat en actualitzar a karmic

# ConvertIT
# deb [http://www.sciallo.net/UbuntuRepo/myrepo](http://www.sciallo.net/UbuntuRepo/myrepo) binary/ # desactivat en actualitzar a lucid

# Spotify
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # desactivat en actualitzar a lucid i reactivat segons [http://www.spotify.com/es/download/previews/](http://www.spotify.com/es/download/previews/)

# Ubuntu-Rescue-Remix
deb [http://ppa.launchpad.net/arzajac/ppa/ubuntu](http://ppa.launchpad.net/arzajac/ppa/ubuntu) lucid main

deb [http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu](http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu) lucid main

Quines línies he de suprimir o comentar?

Gràcies a la bestreta.

---

### Post by wgarcia on 2012-03-28
Navega a 

```
cd /etc/apt
```

i mira si tens una carpeta aquí es diu "sources.list.d". Dins d'aquesta carpeta poden haver-hi altres fonts de programari, i potser alguna d'elles repeteix la que es menciona al principi del missatge que reps. Jo l'esborraria de sources.list i la deixaria en aquesta carpeta.

---

### Post by jinglada on 2012-03-28
> **wgarcia said:**
> Navega a 

```
cd /etc/apt
```

i mira si tens una carpeta aquí es diu "sources.list.d". Dins d'aquesta carpeta poden haver-hi altres fonts de programari, i potser alguna d'elles repeteix la que es menciona al principi del missatge que reps. Jo l'esborraria de sources.list i la deixaria en aquesta carpeta.

Exacte wgarcia, això és el que hi tinc:
[email]joan@joan-laptop:/etc/apt/sources.list[/email].d$ ls -la
total 52
drwxr-xr-x 2 root root 4096 2012-02-28 23:22 .
drwxr-xr-x 6 root root 4096 2012-02-28 23:16 ..
-rw-r--r-- 1 root root   85 2012-02-28 23:22 dropbox.list
-rw-r--r-- 1 root root   48 2011-06-09 20:09 dropbox.list.distUpgrade
-rw-r--r-- 1 root root   85 2012-02-28 23:22 dropbox.list.save
-rw-r--r-- 1 root root  214 2012-02-28 23:22 google-chrome.list
-rw-r--r-- 1 root root  176 2011-06-09 20:09 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  214 2012-02-28 23:22 google-chrome.list.save
-rw-r--r-- 1 root root  180 2012-02-28 23:22 google-talkplugin.list
-rw-r--r-- 1 root root  180 2012-02-28 23:22 google-talkplugin.list.save
-rw-r--r-- 1 root root  172 2012-02-28 23:22 lucid-partner.list
-rw-r--r-- 1 root root  172 2012-02-28 23:22 lucid-partner.list.save
-rw-r--r-- 1 root root   75 2012-02-28 23:22 mscore-ubuntu-mscore-stable-lucid.list

He desactivat les dues últimes línies del /etc/apt/sources.list, he actualitzat el programari i ja no m'ha donat error.

Gràcies wgarcia!

---

### Post by wgarcia on 2012-03-29
D'acord, com pots veure això de "mscore" ho tenies duplicat al fitxer "sources.list" i un altre ".list" que hi ha a la carpeta "sources.list.d". Esborrant a sources.list ja no ho tens duplicat.

---

