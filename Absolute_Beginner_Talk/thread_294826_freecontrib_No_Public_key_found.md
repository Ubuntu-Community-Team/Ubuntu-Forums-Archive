---
title: "freecontrib No Public key found"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by CupofDice on 2006-11-07
I am using Dapper, and yesterday I got this problem when updating/reloading my repository after adding the espergreen (deluge bittorrent) repository.
```
Get:1 http://packages.freecontrib.org dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://packages.freecontrib.org dapper Release
Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.canonical.com dapper-commercial Release
Ign http://qcomicbook.horisone.com dapper Release.gpg
Err http://packages.freecontrib.org dapper Release

Hit http://archive.ubuntu.com dapper-updates Release
Get:7 http://packages.freecontrib.org dapper Release [9452B]
Ign http://qcomicbook.horisone.com dapper Release
Ign http://asher256-repository.tuxfamily.org dapper Release.gpg
Ign http://asher256-repository.tuxfamily.org ubuntu Release.gpg
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Ign http://asher256-repository.tuxfamily.org dapper Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Ign http://asher256-repository.tuxfamily.org ubuntu Release
Ign http://packages.freecontrib.org dapper Release
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://qcomicbook.horisone.com dapper/main Packages
Hit http://packages.freecontrib.org dapper/free Packages
Ign http://asher256-repository.tuxfamily.org dapper/main Packages
Ign http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Ign http://asher256-repository.tuxfamily.org dapper/french Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/main Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/french Packages
Hit http://qcomicbook.horisone.com dapper/main Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://asher256-repository.tuxfamily.org dapper/main Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://packages.freecontrib.org dapper/non-free Sources
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Hit http://asher256-repository.tuxfamily.org dapper/french Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/main Packages
Hit http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://asher256-repository.tuxfamily.org ubuntu/french Packages
Fetched 9646B in 1s (6104B/s)
Reading package lists... Done
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems

```
I just had some espergreen connection problems, so I disabled that.

---

### Post by Ecthelion on 2006-11-07
Your not the only one with that problem...
Maybe it helps to read [this]("http://ubuntuforums.org/showthread.php?p=1693165")...

---

### Post by CupofDice on 2006-11-16
The problem wasn't with deluge, but with freecontrib. Thanks for your help though. Anyway I just came across this solution-
[http://ubuntuforums.org/showthread.php?t=295979&highlight=freecontrib]("http://ubuntuforums.org/showthread.php?t=295979&highlight=freecontrib")
[]("http://ubuntuforums.org/showthread.php?t=295979&highlight=freecontrib")
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```
It worked, and "sudo apt-get update" now works with no errors. I do have a question for anyone reading though. This solution was for the edgy repository, and I use drake. Will I run into any problems? I don't think I should though since this is just a key.

---

