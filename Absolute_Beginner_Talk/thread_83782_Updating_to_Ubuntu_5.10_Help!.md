---
title: "Updating to Ubuntu 5.10 Help!"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-10-29
When I typed "sudo apt-get dist-upgrade" it gave me this
```
tristan@Tristan:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
tristan@Tristan:~$

```
So I typed "sudo apt-get update" and it gave me this
```
tristan@Tristan:~$ sudo apt-get update
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  404 Not Found
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://security.ubuntu.com hoary-security Release
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Get:3 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 4B in 5s (1B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main /binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/univ erse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/mult iverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/rest ricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory )
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
tristan@Tristan:~$
```
What's wrong??
Is it my repositories? Here it is just incase,
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by Xian on 2005-10-29
Just open your sources.list and do two things:

1. Delete the backport entries
2. Change "hoary" to "breezy"

Do the 'apt-get update' session again.
Then 'apt-get dist-upgrade'

---

