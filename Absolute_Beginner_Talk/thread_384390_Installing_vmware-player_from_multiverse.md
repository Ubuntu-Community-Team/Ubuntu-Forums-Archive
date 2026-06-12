---
title: "Installing vmware-player from multiverse"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by carl.davis on 2007-03-14
I am running 6.10 and cannot find vmware-player to install it with apt-get.  This is a new install and I have enabled multiverse and done a sudo apt-get update.  I have 6.10 running on my laptop and vmware-player is installed, however it was installed when I was running Dapper.  Any idea why I cannot find vmware-player?

sudo apt-cache search vmware
xserver-xorg-video-vmware - X.Org X server -- VMware display driver
vmware-player-kernel-modules-2.6.17-10 - vmware-player modules for Linux (kernel 2.6.17)
vmware-player-kernel-modules-2.6.17-11 - vmware-player modules for Linux (kernel 2.6.17)

---

### Post by useResa on 2007-03-14
Indeed seems a bit strange. I have also Edgy and multiverse activated.
```
rdrijsen@rdrijsen-laptop:~$ sudo apt-cache search vmware
xserver-xorg-video-vmware - X.Org X server -- VMware display driver
vmware-player - Free virtual machine player from VMware
vmware-player-kernel-modules-2.6.15-23 - vmware-player modules for Linux (kernel 2.6.15)
vmware-player-kernel-source - Source for the vmware-player-kernel drivers.
vmware-player-kernel-modules-2.6.17-10 - vmware-player modules for Linux (kernel 2.6.17)
vmware-player-kernel-modules-2.6.17-11 - vmware-player modules for Linux (kernel 2.6.17)
vmware-player-kernel-modules - vmware-player kernel module dependency package

```

As a reference please find below the content of my /etc/apt/sources.list
Maybe you can find a difference which may explain why you can not find vmware-player.
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted multiverse universe

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted multiverse universe

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse universe

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Commented next lines out for the Edgy Eft update
## deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
## deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
# deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## BERYL REPOSITORY
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

## WINE REPOSITORY
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

## AMAROK REPOSITORY
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main

## SWIFTFOX REPOSITORY
# deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

## AUTOMATIX REPOSITORY
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

Hope this will help you resolve the matter.

---

### Post by Bachstelze on 2007-03-14
Did you do a *sudo apt-get update* after editing your sources.list ?

---

### Post by useResa on 2007-03-14
> **HymnToLife said:**
> Did you do a *sudo apt-get update* after editing your sources.list ?
According to his post he did
> **carl.davis said:**
> I am running 6.10 and cannot find vmware-player to install it with apt-get. This is a new install and I have enabled multiverse **and done a sudo apt-get update**.

---

