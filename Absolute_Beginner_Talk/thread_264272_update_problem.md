---
title: "update problem"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by turo on 2006-09-24
I am currently running a dual-boot system with WinXP (for the games :D ).  Ubuntu has been working fine for the past couple of weeks until today.  Everytime I try to update, I get the following...

```


sudo apt-get update

Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://archive.ubuntu.com dapper Release.gpg
Ign http://us.archive.ubuntu.com dapper Release.gpg
Ign http://wine.budgetdedicated.com dapper Release.gpg
Ign http://security.ubuntu.com dapper-security Release
Ign http://archive.ubuntu.com dapper Release
Ign http://us.archive.ubuntu.com dapper-updates Release.gpg
Ign http://wine.budgetdedicated.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper/universe Packages
Ign http://us.archive.ubuntu.com dapper Release
Ign http://wine.budgetdedicated.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://us.archive.ubuntu.com dapper-updates Release
Err http://wine.budgetdedicated.com dapper/main Packages
  403 Forbidden
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Err http://archive.ubuntu.com dapper/universe Packages
  403 Forbidden [IP: 195.248.90.54 80]
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  403 Forbidden
Err http://archive.ubuntu.com dapper/main Packages
  403 Forbidden [IP: 195.248.90.54 80]
Ign http://us.archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/restricted Packages
  403 Forbidden
Err http://archive.ubuntu.com dapper/restricted Packages
  403 Forbidden [IP: 195.248.90.54 80]
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/main Sources
  403 Forbidden
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  403 Forbidden
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Err http://us.archive.ubuntu.com dapper/main Sources
  403 Forbidden [IP: 195.248.90.54 80]
Err http://us.archive.ubuntu.com dapper/restricted Sources
  403 Forbidden [IP: 195.248.90.54 80]
Err http://us.archive.ubuntu.com dapper/universe Sources
  403 Forbidden [IP: 195.248.90.54 80]
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  403 Forbidden [IP: 195.248.90.54 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  403 Forbidden [IP: 195.248.90.54 80]
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  403 Forbidden [IP: 195.248.90.54 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  403 Forbidden
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  403 Forbidden
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  403 Forbidden [IP: 195.248.90.54 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  403 Forbidden [IP: 195.248.90.54 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Seems it cannot download any updates.  Any ideas on how to fix this?  Thanks!

-turo

---

### Post by bulldog on 2006-09-24
Make a copy of your sources.list

sudo cd /etc/apt/sources.list /etc/apt/sources.list-backup

I give you a copy of my sources.list which you can put in your's

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main #restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo2
##deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb-src [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./


##Xgl/Compiz
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

##Moblock
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main

##Test
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

##Asher repo's
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

## Canonical commercial repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

see if this works,if it does you can remove the repo's you don't use and copy your own.

---

### Post by turo on 2006-09-24
Well, running sudo apo-get update seems to work now, but now I have another problem.  When I run the update manager, now it sees there are updates to download, but if I try to install the updates I get the following error message:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb
  403 Forbidden [IP: 195.248.90.54 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
  403 Forbidden [IP: 195.248.90.54 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
  403 Forbidden [IP: 195.248.90.54 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
  403 Forbidden [IP: 195.248.90.54 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb
  403 Forbidden [IP: 195.248.90.54 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine_1.4.3-0ubuntu1_i386.deb
  403 Forbidden [IP: 195.248.90.54 80]

```



EDIT: I figured out the problem, it has to do with my network's firewall settings (my internet is provided by my apartment complex).  I followed this and it worked like a charm:

[http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden](http://www.ubuntuforums.org/showthread.php?t=186455&highlight=403+Forbidden)

---

