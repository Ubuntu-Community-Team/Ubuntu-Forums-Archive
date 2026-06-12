---
title: "can't get security packages for feisty"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by eheitner on 2007-05-07
Ok, I am still failing to get security packages for feisty:
****
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
*******

This is my sources.list:
***************
# deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy main restricted universe multiverse
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free
# deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
#
## OFFICIALLY SUPPORTED REPOSITORIES
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted
## COMMUNITY SUPPORTED REPOSITORIES
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe multiverse main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
## BACKPORTS
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
## PENGUIN LIBERATION FRONT (PLF) REPOSITORIES ([http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf))
## Primary
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
## Secondary (use only if primary is not working)
# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) edgy free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) edgy free non-free
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
*******************************

I am using this command line:
gksu "update-manager -c"

---

### Post by zvacet on 2007-05-07
Do you try to upgrade Edgy?I tryed your links and no luck.Coment that lines(put # sign in front of the line)and do zhr same with all unofficial repos.Save source list.

```
sudo aptitude update
```

If you want to do upgrade go to the update manager and you will see window with massage of possible distro upgrade.if you want to accept it and here you go.

---

### Post by NeoLithium on 2007-05-07
The additional repos from automatix could be causing a problem as well. It's best to go with the vanilla sources list from [http://www.ubuntuguide.org](http://www.ubuntuguide.org) 's edgy section, and do it that way.

---

### Post by nyvalbanat on 2007-06-08
The problem is duplicate repositories listed in sources.list. Remove them and retry.

---

