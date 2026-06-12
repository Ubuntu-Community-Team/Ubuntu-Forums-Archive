---
title: "sick sources.list"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-10-27
some issues when i try to update as follows:

Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty Release.gpg [191B]        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/main Translation-en_NZ               
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/restricted Translation-en_NZ 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_NZ                   
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_NZ              
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/universe Translation-en_NZ   
Get:4 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/universe Translation-en_NZ
Get:5 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/main Translation-en_NZ
Hit [http://dl.google.com](http://dl.google.com) stable Release        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/universe Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_NZ 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/deb-src Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/http://packages.medibuntu.org/ Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/feisty Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security Release
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_NZ
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_NZ
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/universe Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/restricted Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty-security/universe Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Fetched 5B in 2s (2B/s)  
Failed to fetch [http://packages.medibuntu.org/dists/feisty/Release](http://packages.medibuntu.org/dists/feisty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

so here is my source.list:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) feisty-security universe
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

thanks :KS

---

### Post by taurus on 2007-10-27
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out the last three repos by placing a # in front of them.

```

#deb http://packages.medibuntu.org/ feisty free non-free 
#deb-src http://packages.medibuntu.org/ feisty free non-free

#deb http://dl.google.com/linux/deb/ stable non-free
```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nixclusive on 2007-10-27
it certainly looks ok to me.. but you can try deleting the files /var/cache/apt/{pkgcache,srcpkgcache}.bin and then run apt-get update again. Don't worry those files will be regenerated. Hope this helps.. just a shot though.

---

### Post by jon zendatta on 2007-10-27
thanks Taurus that worked, i didn't do the upgrade those as i'm happy with fiesty :)

---

### Post by taurus on 2007-10-27
```
sudo apt-get upgrade
```
doesn't mean that it will upgrade your Feisty to Gutsy.  It will upgrade the packages currently on your machine to the latest versions.

---

