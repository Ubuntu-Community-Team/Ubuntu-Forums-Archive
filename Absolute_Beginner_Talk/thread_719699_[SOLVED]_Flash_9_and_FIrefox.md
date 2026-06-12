---
title: "[SOLVED] Flash 9 and FIrefox"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by kidstar64 on 2008-03-09
Hello,

Ok, so i have tried installing flash sooo many diffrent ways. ive tried usinf the mozilla plugin manager, says it cannot install it. Fair enough. so i get the tarball and run the installer but every directory it says it is not a valid directory. sudo apt-get install nonfree-flash or whatever says i allrady have it. I have manually  moved the *.so to the mozilla plugin folder and nothing. 

However, i dont think flash is the only problem. when i try to add remove programms, when i click the check box, it says i need to update, ok. so i update and click the checkbox and it says i need to update. this repeats itself forever. 

Thanks in advance,
Kidstar64

---

### Post by aysiu on 2008-03-09
Those are two separate issues.

First of all, for Flash, run the installer with *sudo* and use the directory /usr/lib/firefox. More details, with screenshots, here:
[http://psychocats.net/ubuntu/flashmanual](http://psychocats.net/ubuntu/flashmanual)

For the second problem, can you copy and paste these commands into the terminal and then copy and paste the output back here? ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by kidstar64 on 2008-03-09
ok

with the flash installation i get the same error

and the output is 
```
mitch@mitch-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://3v1n0.tuxfamily.org edgy 3v1n0
deb-src http://3v1n0.tuxfamily.org edgy 3v1n0
mitch@mitch-laptop:~$ sudo apt-get update
[sudo] password for mitch:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Ign http://3v1n0.tuxfamily.org edgy Release.gpg            
Ign http://3v1n0.tuxfamily.org edgy/3v1n0 Translation-en_CA
Ign http://3v1n0.tuxfamily.org edgy Release
Ign http://3v1n0.tuxfamily.org edgy/3v1n0 Packages
Ign http://3v1n0.tuxfamily.org edgy/3v1n0 Sources
Err http://3v1n0.tuxfamily.org edgy/3v1n0 Packages
  301 Moved Permanently
Err http://3v1n0.tuxfamily.org edgy/3v1n0 Sources
  301 Moved Permanently
Failed to fetch http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/binary-i386/Packages.gz 301 Moved Permanently
Failed to fetch http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/source/Sources.gz 301 Moved Permanently
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
mitch@mitch-laptop:~$ 

```

---

### Post by aysiu on 2008-03-09
Okay, you have two software repository sources enabled--one is Ubuntu 7.10's CD, and the other is an outdated third-party repository for Ubuntu 6.10.

I would suggest you [get a fresh set of repositories](http://www.psychocats.net/ubuntu/sources#key) and try Add/Remove again.

---

### Post by The Titan on 2008-03-09
the best way to install flash is, 
First: do what aysiu said

Second: download the first file on this page. [http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266)

it is an archive of flash player at different revisions.  Install the second oldest revision.  This version runs much better on linux.

---

### Post by kidstar64 on 2008-03-09
that seems to have helped the update issue but flash sitll wont work. any suggestions

---

### Post by The Titan on 2008-03-09
> **kidstar64 said:**
> that seems to have helped the update issue but flash sitll wont work. any suggestions
did you entirely remove flash? synaptic and uncheck flash-nonfree and  Remove the file you manually put in the firefox folder?

---

### Post by kidstar64 on 2008-03-09
Thanks for all of your help. My apt repositories now work as well as flash.

---

### Post by The Titan on 2008-03-09
No prob, just curious what was it?

---

