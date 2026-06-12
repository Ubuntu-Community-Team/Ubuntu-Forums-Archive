---
title: "Repository Problem"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by baillie on 2007-04-02
Hi,

I am having problems downloading the updated repository list, using the synaptic package manager, or through the terminal using apt-get update. Using Synaptic I get the following message, its the same in the terminal.

[IMG]http://img504.imageshack.us/img504/6402/screenshotup7.png[/IMG]

My Sources.list: ```

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

This is a clean install of 6.10, the only thing installed so far was easyubuntu, which was removed again, because I thought it was causing the problem, but I'm still getting the error. How can I get rid of the error, so I can get on with installing the software that I need?

Thanks

---

### Post by NeoLithium on 2007-04-02
One thing you can do, is get a fresh repository list from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  They have one there that is unadulterated and will give you everything a fresh install will need.

---

### Post by baillie on 2007-04-02
> **NeoLithium said:**
> One thing you can do, is get a fresh repository list from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  They have one there that is unadulterated and will give you everything a fresh install will need.
Thanks, should of thought about that before. Updated correctly, and I should be able to install the stuff that I want now.

For anybody with the same problem, I replaced my original sources.list with this one: ```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen
```

---

