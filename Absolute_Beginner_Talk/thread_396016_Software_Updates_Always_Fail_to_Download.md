---
title: "Software Updates Always Fail to Download"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-03-28
Hello.

I have newly installed ubuntu 610 and conected it to the internet. On the upper taskbar, I am notified that there are 62 new software updates available for download.

However, when I attempt to download them (click "Install Upgrades"), it cannot download any of them. When I look at the download manager's "Progress of single files", I can see that all of them failed to download.

What can I do about this?

Anders

---

### Post by johnc4510 on 2007-03-28
In a terminal: Applications>Accessories>Terminal   type this:

sudo gedit /etc/apts/sources.list

Copy the file that opens and paste the output back here please.

---

### Post by ahlandberg on 2007-03-29
The file that opens is empty!

That might be the problem, hey!?

What should I put there??

---

### Post by zvacet on 2007-03-29
[http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories")

---

### Post by ahlandberg on 2007-03-29
The file /etc/apt/sources.list contains the following:

--------------------------------------------------------------------------------------


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by ahlandberg on 2007-03-29
> **zvacet said:**
> [http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories")

I have put the contents of the sources.list file in the guide into my own file and run the update. Some of the updates still cannot be read, is that normal? What is the recommended source list? Is there a standard list?

---

### Post by zvacet on 2007-03-29
There is not such thing as standard source list.You have sources suported by Ubuntu and one wich are not.In unsoported you can get some programs you want to have but from many reasons Ubuntu doesn´t provide them.Did you do this
[https://help.ubuntu.com/community/Repositories/Ubuntu/Breezy]("https://help.ubuntu.com/community/Repositories/Ubuntu/Breezy")

Delete you source list and put one from link I posted to you.here is my source list just for example> # deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ feisty main restricted
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) feisty listen

---

