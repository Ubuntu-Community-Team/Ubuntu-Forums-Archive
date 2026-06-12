---
title: "Command-Line Install: apt-get not working"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by anonim on 2007-04-20
I just finished a command-line install (from the alternate CD) of Feisty Fawn.

I'm trying to get my Atheros wireless card to work. I found the following resource online:
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

During the process, two of the steps are to install the bin86 and the sharutils packages. However, neither of the installs work successfully. Here is what I get:

```
root@xxxxx:/# apt-get -y install build-essential bin86
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bin86
root@xxxxx:/# apt-get -y install sharutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sharutils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.
E: Package sharutils has no installation candidate
root@xxxxx:/#
```

My /etc/apt/sources.list is the default that comes with the installation. I tried downloading the two packages and then adding an entry in the sources.list, but this also didn't work (maybe I didn't do it right - I'm new to linux).

The Ubuntu installation detected my LAN connection and set it up automatically. I can successfully ping us.archive.ubuntu.com.

I should also note that I don't know if the restricted modules are installed by default or not. This is what I get when I try to install it:
```
root@xxxxx:/# apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-restricted-modules-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@xxxxx:/#
```

What do I need to do to get these packages installed?

---

### Post by Comzee on 2007-04-20
Can you get it using aptitude or synaptic?

---

### Post by Seisen on 2007-04-20
Post what your source list looks like.

---

### Post by lamalex on 2007-04-20
do an apt-cache search bin86 to see if it has a slightly different name in the ubuntu repo. then install the correct package.

---

### Post by anonim on 2007-04-20
First of all, thanks for the suggestions...

> **Comzee said:**
> Can you get it using aptitude or synaptic?I installed Ubuntu as a command-line, so I don't have the synaptic package manager. I tried using aptitude - it told me that it could not find either of the packages (bin86 or sharutils).

> **Seisen said:**
> Post what your source list looks like.Here are all non-commented lines:
```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

deb http://us.archive.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu feisty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu feisty-security universe
deb-src http://us.archive.ubuntu.com/ubuntu feisty-security universe
deb http://us.archive.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu feisty-security multiverse
```

> **Iamalex said:**
> do an apt-cache search bin86 to see if it has a slightly different name in the ubuntu repo. then install the correct package.Neither apt-cache search bin86 nor apt-cache search sharutils returned any output, it just put me back at the prompt again. So I assume it did not find these packages in the cache.

Please keep the suggestions coming. Perhaps I need to add other sources besides us.archive.ubuntu.com?

---

### Post by Seisen on 2007-04-20
Use this source list.

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

```

You don't have to use the backports repos or the PLF repos if you don't want to you can just uncomment them.

---

