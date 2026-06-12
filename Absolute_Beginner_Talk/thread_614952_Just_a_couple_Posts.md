---
title: "Just a couple Posts"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by monsieurdozier on 2007-11-16
I've got a couple things.

I tried to do my updates this morning, but three packages won't update.

libsmbclient
samba-common
smbclient

I get a 403 Forbidden error.  They're listed as Important Security updates, so I'd like to get them.


Also, how to I install a program from source code?  I downloaded the TAR for Cinelerra from [Here](http://heroinewarrior.com/cinelerra.php3).  And I was wondering how do I install it from Source Code.

Any help will be greatly appreciated.

Monsieur Dozier

---

### Post by taurus on 2007-11-16
Can you post the exact error message when you run those two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by monsieurdozier on 2007-11-16
This is what I get running sudo apt-get upgrade
> 
XXXX@XXXX:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsmbclient samba-common smbclient
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8606kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main smbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main samba-common 3.0.26a-1ubuntu2.1
  403 Forbidden
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsmbclient 3.0.26a-1ubuntu2.1
  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Sudo apt-get update ran but didn't do anything.

Sudo apt-get upgrade --fix-missing gave me the same errors.

This is my sources.list

> 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


---

### Post by ocgstyles on 2007-11-16
> **monsieurdozier said:**
> I've got a couple things.

I tried to do my updates this morning, but three packages won't update.

libsmbclient
samba-common
smbclient

I get a 403 Forbidden error.  They're listed as Important Security updates, so I'd like to get them.


I tried to install 7.04 on another PC today and get the same errors while running updates.  The file is just not there in the repository:

Errors are:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.24-2ubuntu1.3_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.24-2ubuntu1.3_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.24-2ubuntu1.3_i386.deb)
  403 Forbidden

Keith

---

### Post by Inxsible on 2007-11-16
Have a look at this thread. It seems there is a bug with those samba packages and therefore they have been disabled from the download.

[http://ubuntuforums.org/showthread.php?t=614858](http://ubuntuforums.org/showthread.php?t=614858)

---

### Post by taurus on 2007-11-16
Or [http://www.ubuntu.com/usn/usn-544-1](http://www.ubuntu.com/usn/usn-544-1).

---

### Post by monsieurdozier on 2007-11-16
> **Inxsible said:**
> Have a look at this thread. It seems there is a bug with those samba packages and therefore they have been disabled from the download.

[http://ubuntuforums.org/showthread.php?t=614858](http://ubuntuforums.org/showthread.php?t=614858)

Ah,  I see.  That explains it.  Thanks much.

---

