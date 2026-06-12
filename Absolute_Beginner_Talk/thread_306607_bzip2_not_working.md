---
title: "bzip2 not working"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-11-25
I've just done a fresh install of Edgy, added the Automatix repos to apt, and on reload I got the first sign that something's up...

```
http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
```

It didn't matter about that, 'matix installed fine and installed everything I wanted fine. Now I'm trying to add a Murrine theme to the themes manager, and it says the file (in .tar.bz2 format) is invalid. I can't do *anything* with bzip2s. I've tried reinstalling the bzip2 package, but to no avail.

:confused:

---

### Post by arnieboy on 2006-11-25
post the following:
```
cat /etc/apt/sources.list
```

---

### Post by happy-and-lost on 2006-11-26
```
jo@mithos:~$ cat /etc/apt/sources.list


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://malteo.homelinux.net edgy-malteo extras
deb http://www.getautomatix.com/apt edgy main
deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt dapper main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END
jo@mithos:~$ 

```

---

### Post by arnieboy on 2006-11-26
there are two instances of
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
in /etc/apt/sources.list
delete one of them, save the file and do a
```
sudo apt-get update
```

---

### Post by happy-and-lost on 2006-11-26
Hmm... nope. Now I get...

```

--snip snip---
99% [11 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err http://www.getautomatix.com edgy/main Packages                             
  Sub-process bzip2 returned an error code (2)
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources      
Hit http://security.ubuntu.com edgy-security/universe Sources        
Hit http://security.ubuntu.com edgy-security/multiverse Sources      
Hit http://gb.archive.ubuntu.com edgy-updates/main Sources           
Hit http://gb.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com edgy-updates/universe Sources
Hit http://gb.archive.ubuntu.com edgy-updates/multiverse Sources
Hit http://malteo.homelinux.net edgy-malteo Release
Hit http://malteo.homelinux.net edgy-malteo/extras Packages
Fetched 11B in 1s (8B/s)
Failed to fetch http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

