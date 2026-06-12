---
title: "Broken Package; Can't install anything !"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-12-11
i am trying to install compiz fusion and i get this error

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgnome-desktop-dev: Depends: libgnomeui-dev (>= 2.14.1-1) but it is not going to be installed
  libmetacity-dev: Depends: libgtk2.0-dev (>= 2.4) but it is not going to be installed
  librsvg2-dev: Depends: libgtk2.0-dev (>= 2.8.17-1) but it is not going to be installed
  libwnck-dev: Depends: libgtk2.0-dev (>= 2.8.17-1) but it is not going to be installed
E: Broken packages

i get this error even if i try to install any other application.. how can i fix this ?.. thank you

---

### Post by Partyboi2 on 2007-12-11
try
```
sudo apt-get install -f
```
to fix broken package

---

### Post by HunkieChan on 2007-12-11
uh, no help.. i get the same error

---

### Post by zvacet on 2007-12-11
**synaptic>edit>fix broken paackages**

if that doesn´t work download deps from [here](http://packages.ubuntu.com/).Of course you will type name of package and after that you will see deps marked with red ball.Download what you are missing and that´s it.

---

### Post by HunkieChan on 2007-12-11
weird . i can't install any of em =/

---

### Post by PmDematagoda on 2007-12-11
Post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by gupta_sumesh63 on 2007-12-11
This is a problem with feisty. Certain packages with old dependencies have been removed to add fresh versions for Gutsy. For this reason there are unmet dependencies. However you can get these packages from sites maintained by the community. You can google for the package and download them from community sites. Hope this helps.

Secondly try the following code in a terminal and try to reinstall packages again.
code:
> sudo dpkg --configure -a

---

### Post by zvacet on 2007-12-11
> This is a problem with feisty. Certain packages with old dependencies have been removed to add fresh versions for Gutsy.

This mean that Feisty is not supported anymore wich is not truth.Only reason for not be able to download packages from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") can be your internet connection or server problems.In short packages ar there but you have to be very carefully to download all dependencies.Just for example if you want to download and install **libgnomeui-dev** you have to go [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgnome-desktop-dev&searchon=names&subword=1&version=feisty&release=all) click and you will see [this](http://packages.ubuntu.com/feisty/libdevel/libgnome-desktop-dev).Now click on** libgnomeui-dev** and you will see all dependencies you have to install.Maybe you don´t need to download them all because you may have them installed allready.You can chek that with synaptic.

---

### Post by HunkieChan on 2007-12-11
> **PmDematagoda said:**
> Post the result of:-

```
cat /etc/apt/sources.list
```

```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main restricted #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu feisty-security universe
# deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
# deb http://edevelop.org/pkg-e/ubuntu feisty e17
# deb http://e17.dunnewind.net/ubuntu feisty e17
# deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
deb http://www.getautomatix.com/apt feisty main

deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END

# deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
# deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
# deb http://ppa.launchpad.net/amaranth/ubuntu feisty main

```

---

### Post by HunkieChan on 2007-12-11
> **gupta_sumesh63 said:**
> This is a problem with feisty. Certain packages with old dependencies have been removed to add fresh versions for Gutsy. For this reason there are unmet dependencies. However you can get these packages from sites maintained by the community. You can google for the package and download them from community sites. Hope this helps.

Secondly try the following code in a terminal and try to reinstall packages again.
code:

i tried that.. i tried to install packages but it says i can't .. i also downloaded dependencies  and tried to install em but still doesnt work.

---

### Post by gupta_sumesh63 on 2007-12-11
What is the error shown when you try to install the downloaded dependencies?
I hope you are using Gdebi package installer to install them.
Or you can use
sudo dpkg -i package_name to install.
once downloaded, I think sources.lst has no role to play.

---

### Post by zvacet on 2007-12-12
Remove Automatix and in source list remove all Automatix related.

```
sudo apt-get update
```

---

### Post by HunkieChan on 2007-12-13
thanks guys.. but i reinstalled feisty fawn again. everything is fine now :)

---

