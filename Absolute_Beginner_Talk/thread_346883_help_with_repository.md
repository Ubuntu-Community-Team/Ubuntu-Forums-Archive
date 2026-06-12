---
title: "help with repository"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by bailey_jatt on 2007-01-26
hi everyone. total linux noob here. just installed ubuntu edgy. did a bit of searching on the internet for being able to play streaming media (like movie trailers) and the works. got to a link saying installing easyubuntu will help out with all the nitty gritties. Anyways i made changes to my repository sources list file to include the newer ones. I think i bungled it up big  time as doing a sudo apt-get update gives me the following error now.


```
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Get:10 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 12B in 1s (7B/s)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing kubuntu-desktop (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```


So could any one give me a copy of their source list which has all the required repository's or tell me a work around for this. I figure the error is something to do with the file. i guess i have added multiple versions of the same thing..Correct me if i am wrong :) 

cheers
bailey

---

### Post by jvc26 on 2007-01-26
If you want the usual sources.list including the one for automatix:
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

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

##Automatix Download
deb http://www.getautomatix.com/apt edgy main

```
Then:
```

wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -

```
To get the automatix key. Also you need the plf key:
```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

```
Then:
```

sudo apt-get update

```
That should work.
Il

---

### Post by bailey_jatt on 2007-01-26
danke :)
its working fine now.. updating as normal

---

### Post by PriceChild on 2007-01-26
In the future I'd reccomend you using the source-o-matic: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by bailey_jatt on 2007-01-26
thanks for the link

---

