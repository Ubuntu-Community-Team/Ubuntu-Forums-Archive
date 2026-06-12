---
title: "update errors in Synaptic manager"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by rrp on 2006-09-03
What do I do about the errors in dapper/binary-amd64 and commercial and main repositories?

---

### Post by croak77 on 2006-09-03
What are the errors?

---

### Post by rrp on 2006-09-03
duplicate sourses and that the repositories are either old or no longer available

---

### Post by croak77 on 2006-09-03
Let's have a look at your /etc/apt/sources.list.

---

### Post by croak77 on 2006-09-03
Also. open a terminal and type;
```
sudo apt-get update
```

Post the entire error message

---

### Post by rrp on 2006-09-03
rrp@rrp-desktop:~$ sudo apt-get update
Err http: archive.canonical.com/ubuntu Release.gpg
  Could not resolve 'dists'
Ign http: archive.canonical.com/ubuntu Release
Ign http: archive.canonical.com/ubuntu/dapper Packages
Ign http: archive.canonical.com/ubuntu/commercial Packages
Ign http: archive.canonical.com/ubuntu/main Packages
Err http: archive.canonical.com/ubuntu/dapper Packages
  Could not resolve 'dists'
Err http: archive.canonical.com/ubuntu/commercial Packages
  Could not resolve 'dists'
Err http: archive.canonical.com/ubuntu/main Packages
  Could not resolve 'dists'
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 6B in 2s (3B/s)
Failed to fetch [http://dists/archive.canonical.com/ubuntu/Release.gpg](http://dists/archive.canonical.com/ubuntu/Release.gpg)  Could not resolve 'dists'
Failed to fetch [http://dists/archive.canonical.com/ubuntu/dapper/binary-amd64/Packages.gz](http://dists/archive.canonical.com/ubuntu/dapper/binary-amd64/Packages.gz)  Could not resolve 'dists'
Failed to fetch [http://dists/archive.canonical.com/ubuntu/commercial/binary-amd64/Packages.gz](http://dists/archive.canonical.com/ubuntu/commercial/binary-amd64/Packages.gz)  Could not resolve 'dists'
Failed to fetch [http://dists/archive.canonical.com/ubuntu/main/binary-amd64/Packages.gz](http://dists/archive.canonical.com/ubuntu/main/binary-amd64/Packages.gz)  Could not resolve 'dists'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by croak77 on 2006-09-03
You have AMD 64 right? Can you post your /etc/apt/sources.list? As you can see [http://dists/archive.canonical.com/](http://dists/archive.canonical.com/) is not a proper URL (note [http://dists/](http://dists/)).

---

### Post by nickpaton on 2006-09-03
As Croak77 asked could you also post the output of:

```
gksudo gedit /etc/apt/sources.list
```

I guess either the Canonical server is down or there's a problem with your repo list

Sorry I see Croak beat me to it!

---

### Post by rrp on 2006-09-03
It won't display anything. thanks.

---

### Post by nickpaton on 2006-09-03
> **rrp said:**
> It won't display anything. thanks.

Mmmm strange; can you do a copy from this post of the whoel command and paste into the Terminal?

BTW - welcome to the forums too!

---

### Post by rrp on 2006-09-03
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb http:// archive.canonical.com/ubuntu dapper commercial main
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted

---

### Post by rrp on 2006-09-03
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb http:// archive.canonical.com/ubuntu dapper commercial main
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb http:// archive.canonical.com/ubuntu dapper commercial main
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted

---

### Post by rrp on 2006-09-03
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb http:// archive.canonical.com/ubuntu dapper commercial main
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb http:// archive.canonical.com/ubuntu dapper commercial main
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted

---

### Post by rrp on 2006-09-03
rrp@rrp-desktop:~$ gksudo gedit /etc/apt/sources.list
(gedit:10484): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
rrp@rrp-desktop:~$ gksudo gedit /etc/apt/sources.list

---

### Post by nickpaton on 2006-09-03
Please backup your existing Repository:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

There appears to be an error in the lines referring to Canonical:

```
deb http:// archive.canonical.com/ubuntu dapper commercial main
```

Please open your sources list and change those lines for:

```
http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/
```

I know that they get you into the Canonical site but I'm not 100% sure that it is the correct place for AMD64.

Can anyone else confirm?

In the meantime suggest you try and see what happens.

---

### Post by rrp on 2006-09-03
Did not work,thanks.

---

### Post by croak77 on 2006-09-04
> **rrp said:**
> Did not work,thanks.

Try this; this is based off what you had minus the duplicate and triplicate repos and the empty spaces.

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

##Ubuntu Security
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://archive.canonical.com/ubuntu dapper commercial main

##Cdrom
##deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted

```

---

