---
title: "Error: Could Not Download All Repository Indexes!"
date: 2008-02-23
forum: Apple PPC Users
---

### Post by GilloD on 2008-02-23
I am a complete n00b to Ubuntu, so I may need some hand holding! I went to install WINE, followed all of the instructions and ran into some problems. If I use the terminal,  I get this:

```
scottstephan@ubuntu:~$ sudo apt-get upgrade  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scottstephan@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc (20071016) gutsy/restricted Translation-en_US
Get:1 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                 
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_US               
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Get:3 http://ports.ubuntu.com gutsy Release.gpg [191B]                         
Ign http://ports.ubuntu.com gutsy/main Translation-en_US                       
Ign http://ports.ubuntu.com gutsy/restricted Translation-en_US                 
Get:4 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Hit http://wine.budgetdedicated.com gutsy Release                              
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://ports.ubuntu.com gutsy/universe Translation-en_US                   
Ign http://ports.ubuntu.com gutsy/multiverse Translation-en_US     
Get:5 http://ports.ubuntu.com gutsy-updates Release.gpg [191B]     
Ign http://ports.ubuntu.com gutsy-updates/main Translation-en_US   
Ign http://ports.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://ports.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://ports.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US   
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US   
Get:6 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]   
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US 
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Get:7 http://ports.ubuntu.com gutsy-security Release.gpg [191B]     
Ign http://ports.ubuntu.com gutsy-security/main Translation-en_US   
Ign http://ports.ubuntu.com gutsy-security/restricted Translation-en_US
Hit http://archive.ubuntu.com gutsy Release                         
Ign http://ports.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://ports.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://ports.ubuntu.com gutsy Release                           
Hit http://ports.ubuntu.com gutsy-updates Release                   
Hit http://archive.ubuntu.com gutsy-updates Release                 
Hit http://ports.ubuntu.com gutsy-security Release                  
Hit http://security.ubuntu.com gutsy-security/universe Packages     
Hit http://archive.ubuntu.com gutsy/universe Packages                          
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://ports.ubuntu.com gutsy/main Packages                                
Hit http://archive.ubuntu.com gutsy/main Packages                   
Hit http://archive.ubuntu.com gutsy/restricted Packages             
Hit http://archive.ubuntu.com gutsy/multiverse Packages             
Hit http://ports.ubuntu.com gutsy/restricted Packages               
Ign http://ports.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Packages       
Hit http://archive.ubuntu.com gutsy-updates/main Packages           
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages     
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages     
Ign http://ports.ubuntu.com gutsy/restricted Sources                
Hit http://ports.ubuntu.com gutsy/universe Packages
Ign http://ports.ubuntu.com gutsy/universe Sources
Hit http://ports.ubuntu.com gutsy/multiverse Packages
Ign http://ports.ubuntu.com gutsy/multiverse Sources
Hit http://ports.ubuntu.com gutsy-updates/main Packages
Hit http://ports.ubuntu.com gutsy-updates/restricted Packages
Ign http://ports.ubuntu.com gutsy-updates/main Sources
Ign http://ports.ubuntu.com gutsy-updates/restricted Sources
Hit http://ports.ubuntu.com gutsy-updates/universe Packages
Ign http://ports.ubuntu.com gutsy-updates/universe Sources
Hit http://ports.ubuntu.com gutsy-updates/multiverse Packages
Ign http://ports.ubuntu.com gutsy-updates/multiverse Sources
Err http://ports.ubuntu.com gutsy/main Sources
  404 Not Found
Hit http://ports.ubuntu.com gutsy-security/main Packages
Hit http://ports.ubuntu.com gutsy-security/restricted Packages
Ign http://ports.ubuntu.com gutsy-security/main Sources
Ign http://ports.ubuntu.com gutsy-security/restricted Sources
Hit http://ports.ubuntu.com gutsy-security/universe Packages
Ign http://ports.ubuntu.com gutsy-security/universe Sources
Hit http://ports.ubuntu.com gutsy-security/multiverse Packages
Ign http://ports.ubuntu.com gutsy-security/multiverse Sources
Err http://ports.ubuntu.com gutsy/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy/universe Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy/multiverse Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/main Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/universe Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-updates/multiverse Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/main Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/restricted Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/universe Sources
  404 Not Found
Err http://ports.ubuntu.com gutsy-security/multiverse Sources
  404 Not Found
Fetched 7B in 1s (4B/s)  
Failed to fetch http://wine.budgetdedicated.com/apt/dists/gutsy/Release  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

If I go through the Package Manager, I get this: ```
http://wine.budgetdedicated.com/apt/dists/gutsy/Release: Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/restricted/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/restricted/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz: 404 Not Found
http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz: 404 Not Found

```

Looks like the same problem, but what's the solution? Seems to be a 404 thing, but how do I change to server or find an alternate source? Thanks!

---

### Post by GilloD on 2008-02-23
Here's my source file. Also, those websites literally no longer exist. Ugh! What now?

```
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release powerpc (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports/ gutsy main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy universe
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-backports main restricted universe multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ gutsy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe main restricted multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ gutsy-security multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
```

---

### Post by el toro on 2008-02-23
I did some looking, and as far as I can tell by looking @ the wine repo, there's no gutsy powerpc release for WINE. Sorry. 

As far as the ubuntu-ports repo goes, [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) resolves fine for me. The 404 errors seem to be for the deb-src lines in your sources.list, as there are no source packages on those powerpc repos. Sorry I can't be of more help.

---

