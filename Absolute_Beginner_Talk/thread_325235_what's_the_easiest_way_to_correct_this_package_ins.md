---
title: "what's the easiest way to correct this package install"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-12-25
liblame-dev:
  Depends: liblame0 (=3.96.1-2) but 3.97-0ubuntu0seveas1 is to be installed

I need to install the liblame-dev package for something i'm trying to compile

i've tried sudo apt-get install -f liblame-dev

then i thought i'd just remove liblame0 then reinstall it but it wants to remove alot of other apps as well

---

### Post by Perfect Storm on 2006-12-25
```
cat /etc/apt/sources.list
```

---

### Post by lime4x4 on 2006-12-25
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen
# deb [http://www.getautomatix.com/apt/](http://www.getautomatix.com/apt/) edgy main

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

#deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy
# deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas custom extras seveas-meta
# deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas custom extras seveas-meta
#deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
#deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
#deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
#deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
#deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17



#AUTOMATIX REPOS END

---

### Post by Perfect Storm on 2006-12-25
Wow, looks like a big mess, no wonder ^^

goto  [http://packages.ubuntu.com/](http://packages.ubuntu.com/) find the package(s) and do a downgrade of the specfic packages.

---

### Post by konst88 on 2006-12-25
Try to use aptitude instead of apt-get. It may help solving the dependency problem.

---

