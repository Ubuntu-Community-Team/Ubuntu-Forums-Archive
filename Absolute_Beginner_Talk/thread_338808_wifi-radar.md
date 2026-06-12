---
title: "wifi-radar"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-15
Hi all , I have just reinstall ubuntu 6.10 but i can't find some packege i downloaded them last week using apt-get !!!!! 
one of them is wifi-radar which i really need to fix the problem of accessing secured wireless network. Also bitchx is not there!!! 

Anyone any answer ???

---

### Post by rabid9797 on 2007-01-15
make sure all the repos are open

```

sudo gedit /etc/apt/sources.list

```

remove the #'s from all the line(except comment lines of course)

---

### Post by Mba7eth on 2007-01-15
> 
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy universe
 deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://kw.archive.ubuntu.com/ubuntu/](http://kw.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

This is the current list (after the modification)  but no sign for wifiradar  using apt-get nor apt-cache :(????????????? 
please i need help guys  ](*,) 


Mba7eth

---

### Post by rabid9797 on 2007-01-15
im not sure what the kw. prefix on all of your url's is, maybe a location prefix?(different country other than US?)

anyway, i checked synaptic and i had it, so here are the other repo's i have besides the ones you have listed. add these and see if it shows up:

```

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

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by puneit on 2007-01-15
Just wondering....
did you ```
sudo apt-get update
``` after modifying the sources:-k

---

### Post by Mba7eth on 2007-01-15
Thanx dud what i miss was this update :) 

but Before i didn't this change in the sources.list file and i got both packages !!! 
just wondering if you have any answer :) 

thanx again for all of you guys

Mba7eth

---

