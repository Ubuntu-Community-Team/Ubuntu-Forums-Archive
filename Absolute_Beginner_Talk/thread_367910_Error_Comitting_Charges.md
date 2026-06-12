---
title: "Error Comitting Charges"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Adra287 on 2007-02-22
When I try to download something with Adept I get the error Message:
[INDENT][/INDENT]There was an error commiting changes. Possibly there was a problem downloading some packages OR the commit would break packages.

---

### Post by aysiu on 2007-02-23
Can you post the terminal output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by Adra287 on 2007-02-23
******@******-desktop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Get:5 [http://kubuntu.org](http://kubuntu.org) edgy Release.gpg [189B]
Ign [http://kubuntu.org](http://kubuntu.org) edgy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Ign [http://kubuntu.org](http://kubuntu.org) edgy/main Translation-en_US
Get:6 [http://kubuntu.org](http://kubuntu.org) edgy Release.gpg [189B]
Ign [http://kubuntu.org](http://kubuntu.org) edgy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://kubuntu.org](http://kubuntu.org) edgy Release
Hit [http://kubuntu.org](http://kubuntu.org) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) edgy/main Packages
Fetched 6B in 41s (0B/s)
Reading package lists... Done
******@******-desktop:~$ cat /etc/apt/sources.list
deb [http://kubuntu.org/packages/kde-356](http://kubuntu.org/packages/kde-356) edgy main
deb [http://kubuntu.org/packages/kde-356](http://kubuntu.org/packages/kde-356) edgy main
deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

---

### Post by Adra287 on 2007-02-27
My version of adept stopped giving me error messages and now it won't even get past downloads.

---

### Post by BWF89 on 2007-11-16
I'm having the same problem also starting yesterday. Could this have anything to do with me having installed Automatix a couple weeks ago?

> **aysiu said:**
> Can you post the terminal output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```
Heres mine:

```
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Get:4 http://packages.medibuntu.org gutsy Release.gpg [189B]
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:5 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Hit http://archive.canonical.com gutsy Release
Ign http://packages.medibuntu.org gutsy/free Translation-en_US
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:6 http://archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_US
Hit http://security.ubuntu.com gutsy-security/main Packages
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://archive.canonical.com gutsy/partner Packages
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Get:7 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Err http://packages.medibuntu.org gutsy Release

Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US
Get:8 http://www.getautomatix.com gutsy Release.gpg [189B]
Ign http://www.getautomatix.com gutsy/main Translation-en_US
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com gutsy Release
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.ubuntu.com gutsy-security Release
Hit http://archive.ubuntu.com gutsy-backports Release
Get:9 http://packages.medibuntu.org gutsy Release [2723B]
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://archive.ubuntu.com gutsy/universe Packages
Ign http://packages.medibuntu.org gutsy Release
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://archive.ubuntu.com gutsy-updates/universe Packages
Hit http://www.getautomatix.com gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Hit http://archive.ubuntu.com gutsy-updates/universe Sources
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.ubuntu.com gutsy-security/main Packages
Hit http://archive.ubuntu.com gutsy-security/restricted Packages
Hit http://archive.ubuntu.com gutsy-security/main Sources
Hit http://archive.ubuntu.com gutsy-security/restricted Sources
Hit http://archive.ubuntu.com gutsy-security/universe Packages
Hit http://archive.ubuntu.com gutsy-security/universe Sources
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Hit http://archive.ubuntu.com gutsy-security/multiverse Sources
Hit http://archive.ubuntu.com gutsy-backports/main Packages
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://archive.ubuntu.com gutsy-backports/universe Packages
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://www.getautomatix.com gutsy/main Packages
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages
Fetched 2919B in 1s (2170B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
```

I tried runnign **apt-get update** like it said but ended up getting this:
```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```

---

### Post by lemming552 on 2007-11-17
Post #2 in [This thread](http://ubuntuforums.org/showthread.php?t=420759) solved it for me.

> **falm said:**
> Hello,
i had the same problem, after

sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
  -> read the output, you will have to answer a few questions
sudo dpkg --configure --pending

everything is working again

---

### Post by BWF89 on 2007-11-17
That seemed to work. Although I'm still not sure what exactly the problem was and what exactly those commands did to solve it.

---

### Post by Adra287 on 2007-11-18
I no longer use ubuntu i have switched due to way too many problems and not enough USER SUPPORT I have basic programing skills but not enough to fix the _**many problems**_ I had

---

