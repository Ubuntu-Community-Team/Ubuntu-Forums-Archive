---
title: "Firefox 1.5 repository update problem"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by CupofDice on 2006-11-21
I got Software Updates open and it wants to install the following-
[IMG]http://i3.photobucket.com/albums/y63/ShadowTitan/Screenshots/SoftwareUpdate1.png[/IMG]
The problem is that I have Firefox 2.0. My repositories are-
```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
##  deb-src http://packages.freecontrib.org/plf dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://qcomicbook.horisone.com/ dapper main
## deb-src http://qcomicbook.horisone.com/ dapper main
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
deb http://deluge.mynimalistic.net/apt dapper main
deb http://users.musicbrainz.org/~luks/ubuntu dapper main
deb http://theli.free.fr/packages/ dapper listen

```
I just commented the asher256 repository a few moments ago (updating list afterwards, but the updates are still there. Should I install, then upgrade back to 2.0 using sudo firefox. I am not really against this idea since Firefox seems a bit broken on me with addons not uninstalling, or installing correctly.

---

