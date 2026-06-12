---
title: "dependency problems"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by billybag on 2006-12-20
i had the problem before, but it was worse so i totally reinstalled edgy and now i am getting it AGAIN

root@billybag-laptop:/home/billybag# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-control-center: Depends: capplets-data (= 1:2.16.1-0ubuntu4.1) but 1:2.16.1-0ubuntu4 is installed
  openoffice.org: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-base: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-calc: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-evolution: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
  python-uno: Depends: openoffice.org-core (= 2.0.4-0ubuntu3) but 2.0.4-0ubuntu2 is installed
E: Unmet dependencies. Try using -f.

root@billybag-laptop:/home/billybag# apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  capplets-data gnome-applets gnome-applets-data gnome-netstatus-applet
  gnome-panel gnome-panel-data gnome-system-tools libpanel-applet2-0
  libtotem-plparser1 openoffice.org-core synaptic system-tools-backends totem
  totem-gstreamer totem-mozilla vino
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
Need to get 0B/47.6MB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg exited unexpectedly

root@billybag-laptop:/home/billybag# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  capplets-data openoffice.org-core
The following packages will be upgraded:
  capplets-data openoffice.org-core
2 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
22 not fully installed or removed.
Need to get 0B/34.1MB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Sub-process /usr/bin/dpkg exited unexpectedly
root@billybag-laptop:/home/billybag# 

AGH what is going on?

---

### Post by Bachstelze on 2006-12-20
Could you please paste the contents of /etc/apt/sources.list ?

---

### Post by billybag on 2006-12-20
> **HymnToLife said:**
> Could you please paste the contents of /etc/apt/sources.list ?
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

---

### Post by billybag on 2006-12-20
also, the command 'dpkg -l | grep -v ^ii' doesn't bring up anything

---

