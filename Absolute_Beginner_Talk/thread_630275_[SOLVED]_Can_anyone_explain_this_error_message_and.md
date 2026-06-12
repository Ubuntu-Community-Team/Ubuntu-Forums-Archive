---
title: "[SOLVED] Can anyone explain this error message and how to fix it?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-12-03
If I try to install pretty much anything through Synaptic, or, as I have just discovered, I try to install any of the automatic updates, I get this error message (attached screenshots).  

This latest manifestation occured whilst trying to install e-uae from the repositories through synaptic.  

Anyone know how I can fix it?

---

### Post by Pumalite on 2007-12-03
Try first:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

report back with output.

---

### Post by philinux on 2007-12-03
What sources have you got listed. I can only find uae in my synaptic

---

### Post by MikeSz on 2007-12-03
Hi Pumalite - on the first bit, here's what I got...

zer0cool@zer0cool:~$ sudo dpkg --configure -a
[sudo] password for zer0cool:
Setting up phpgroupware (0.9.16.012+dfsg-1) ...
setting up apache
setting up apache-ssl
setting up apache-perl
setting up apache2
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
/usr/share/wwwconfig-common/pgsql.get: line 77: psql: command not found
dpkg: error processing phpgroupware (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of phpgroupware-sitemgr:
 phpgroupware-sitemgr depends on phpgroupware (>= 0.9.16); however:
  Package phpgroupware is not configured yet.
dpkg: error processing phpgroupware-sitemgr (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 phpgroupware
 phpgroupware-sitemgr
zer0cool@zer0cool:~$ 

doing the rest as we speak.  

On the repo's  Havent added any other than the medibuntu ones for the multimedia.  Other than that, they are all standard.  I can post my etc/apt/sources.list if that helps?

---

### Post by MikeSz on 2007-12-03
and here they are....

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Pumalite on 2007-12-03
sudo dpkg --remove --force-remove-reinstreq phpgroupware-sitemgr
Then reinstall as needed.

---

### Post by perce on 2007-12-03
You could also try to comment the first line:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

in your source.list, then run 
sudo apt-get update
sudo apt-get install -f

---

### Post by MikeSz on 2007-12-04
well - after a lot (and I mean a lot) of messing about, ive sorted it out - the easy way that was to simply back everything up onto a memory stick and install from scratch!  A bit defeatist I know but I tried those suggestions and they didnt seem to cure it.  Anyway, I have a fresh install and everything's working fine (until I break it again...)  Thanks both for your help

---

