---
title: "using ' unstable' debs killed edgy"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Evil Dax on 2006-12-11
I was trying to get a nightly build of VLC to work, as my S/PDIF under VLC was no longer functioning.
Doing so I had to use a lot of .debs from the 'unstable' branch of debian.org.
After that, I was unable to compile a new CVS of linuxdcpp, 
it was naggin' about libglide-2.0
So, I tried to fix that with another 'unstable' deb, causing my PC to go almost completely berserk.
Apt-get update, upgrade, and dist-upgrade do no longer work:
apt-get upgrade gives this:
```

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
21 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (2.0.4-0ubuntu3) ...
Updating fontconfig cache...
"/usr/share/fonts": error scanning
"/usr/X11R6/lib/X11/fonts": error scanning
"/usr/local/share/fonts": error scanning
"/var/lib/defoma/fontconfig.d": error scanning
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.0.4); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.0.4~rc3) | openoffice.org-core-experimental (>> 2.0.4~rc3); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-en-gb:
 openoffice.org-l10n-en-gb depends on openoffice.org-common (>= 2.0.4~rc3) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not installed.
 openoffice.org-l10n-en-gb depends on openoffice.org-common (<< 2.0.5) | language-support-en; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-en is not installed.
dpkg: error processing openoffice.org-l10n-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-es:
 openoffice.org-l10n-es depends on openoffice.org-common (>= 2.0.4~rc3) | language-support-es; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-es is not installed.
 openoffice.org-l10n-es depends on openoffice.org-common (<< 2.0.5) | language-support-es; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-es is not installed.
dpkg: error processing openoffice.org-l10n-es (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-l10n-nl:
 openoffice.org-l10n-nl depends on openoffice.org-common (>= 2.0.4~rc3) | language-support-nl; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-nl is not installed.
 openoffice.org-l10n-nl depends on openoffice.org-common (<< 2.0.5) | language-support-nl; however:
  Package openoffice.org-common is not configured yet.
  Package language-support-nl is not installed.
dpkg: error processing openoffice.org-l10n-nl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-hicontrast:
 openoffice.org-style-hicontrast depends on openoffice.org-common (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-hicontrast (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-default:
 openoffice.org-style-default depends on openoffice.org-common (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-default (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-industrial:
 openoffice.org-style-industrial depends on openoffice.org-common (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-industrial (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 2.0.4-0ubuntu3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-base
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-evolution
 openoffice.org-gtk
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-math
 python-uno
 openoffice.org-writer
 openoffice.org-common
 openoffice.org-l10n-en-gb
 openoffice.org-l10n-es
 openoffice.org-l10n-nl
 openoffice.org-java-common
 openoffice.org-style-hicontrast
 openoffice.org-style-default
 openoffice.org-style-industrial
 openoffice.org-style-crystal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so, I tried to re-install openoffice.
That didn't work also. Just like apt-get install -f and apt-get autoremove.

Is there any way to get the 'normal' repos back ?

I now am running in fail-safe gnome, the only option alive....
:( 

Running 'Edgy' Ubuntu 6.10

---

### Post by kinematic on 2006-12-11
go to the shell and use this command to edit your sources.list
> sudo nano -w /etc/apt/sources.list
edit out debian unstable and close and save with crtl>x
and now you also know why it's called debian unstable....at times it can bork a debian box so just imagine what it can do to ubuntu ;)

---

### Post by Evil Dax on 2006-12-11
Well, that's seems to be the problem, I've manually downloaded and installed those unstable .debs without putting them into sources.list.
In my sources.list only the 'normal' repos are there (universe multiverse restricted):
```

# deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main multiverse restricted universe
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports main multiverse restricted universe #Added by software-properties

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse #Added by software-properties
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse


deb http://archive.ubuntu.com/ubuntu/ edgy restricted multiverse main universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy restricted multiverse main universe

deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe


#User-defined crap

#Beryl
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl/ edgy main-edgy
# deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy
# deb http://ubuntu.compiz.net/ edgy main-edgy
# deb http://amaranth.selfip.com edgy lrm
# deb http://ubuntu.beryl-project.org/ edgy main

#nVidia
deb http://seerofsouls.com/ edgy contrib

#uShare
# deb http://www.geexbox.org/debian/ unstable main

#wine
deb http://wine.budgetdedicated.com/apt edgy main

# Videolan
deb http://nightlies.videolan.org/build/dapper-i386 /
# deb http://nightlies.videolan.org/build/exp-i386/arch ./
# deb http://nightlies.videolan.org/build/sid-i386/arch ./

```

---

### Post by kinematic on 2006-12-11
then you can do a search in apt.
> sudo apt-cache search packagename(or approximate packagename)
that will give a list of packages matching the search criteria and then to remove it
> sudo apt-get remove --purge packagename
i don't know if this will fix it because as i said unstable can seriously bork a debian box so i don't know what kind of havoc it could wreak on ubuntu.

---

### Post by Evil Dax on 2006-12-11
hmm... apt-cache search didn't bring up anything..
Stubborn as I am, I've put the debian unstable into sources.list.
](*,) 
570 or so updates later (and a few hours..), it does not do me much good, crashes 10sec after GRUB loads, saying something about a mount point missing...

Ow well, downloading 6.10 now from a WXP machine..

* and yet another thing learned *

---

### Post by angkor on 2006-12-11
> **Evil Dax said:**
> * and yet another thing learned *

Yup, **don't** mix debian repos (or debs for that matter) with ubuntu repositories.

---

