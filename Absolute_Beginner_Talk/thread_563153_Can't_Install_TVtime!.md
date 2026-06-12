---
title: "Can't Install TVtime!"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-29
I have A winfast pvr TV2000 XP series and I want to install tvtme to watch tv on. This is waht I get:

```
niko@home:~$ sudo apt-get install tvtime aumix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tvtime
niko@home:~$ 

```:confused:

---

### Post by CaptainInsaneO on 2007-09-29
In synaptic, go to Settings>Repositories and make sure all your repo's are checked.

---

### Post by Gavin77 on 2007-09-29
Make sure you have the universe repository enabled, I just checked and it's there.

---

### Post by nikoPSK on 2007-09-30
I checked universe (none of the ones were checked for some reason...) And I cliked okay then reload and I get this

```
Could not download all repository indexes
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
ary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]
http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.89.6 80]

```

:confused: You scwewy ubuntu!

---

### Post by mcduck on 2007-09-30
Support for Breezy ended in April 13, 2007, so it's repositories are closed.

You should install a bit more up-to-date version of Ubuntu..

---

### Post by nikoPSK on 2007-09-30
Like what? I have 7.04... I don't use breezy.:confused:

---

### Post by mcduck on 2007-09-30
> **nikoPSK said:**
> Like what? I have 7.04... I don't use breezy.:confused:

Then your sources.list is wrong as apt its trying to install things from Breezy's repositories.

Could you post here then contents of /etc/apt/sources.list file?

---

### Post by nikoPSK on 2007-09-30
Nvm I got tvtime working... But no sound! And our place we live in has a security camera at the front door (we're on the 10th floor) its on like channel 118 but I don't know where to configure that:confused:

(I did a channel scan but it doesn't seem to scan past 100)

---

