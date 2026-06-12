---
title: "updating"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by gideon793 on 2008-02-13
i have just recently installed ubuntu. i connect to the internet through a proxy server and am able to use firefox without any problems. however, when i try to use synaptic or to install any programs i get the following error, in spite of entering the correct proxy settings:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by jan quark on 2008-02-13
perhaps your sources are not enabled

run this in terminal, perhaps it helps

```
sudo apt-get update
```

if not please post the output of this terminal command

```
cat /etc/apt/sources.list
```

---

### Post by gideon793 on 2008-02-13
Im getting the following error:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security multiverse
gideon793@gideon793:~$ sudo apt-get update
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/multiverse Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/universe Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/main Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/restricted Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/universe Sources
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Packages
  407 Proxy Access Denied
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-security/multiverse Sources
  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  407 Proxy Access Denied
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  407 Proxy Access Denied
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by erginemr on 2008-02-13
If you are sure that it is not the proxy, try changing your main repository server from "Software Resources" as attached.

---

