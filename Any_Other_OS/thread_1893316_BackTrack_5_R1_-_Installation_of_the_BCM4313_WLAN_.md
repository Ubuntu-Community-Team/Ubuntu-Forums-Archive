---
title: "BackTrack 5 R1 - Installation of the BCM4313 WLAN Controller"
date: 2011-12-10
forum: Any Other OS
---

### Post by nikkon1988 on 2011-12-10
Hi, I have been trying to install my wireless controller for the past few days (I'm new to the linux world). My WLAN controller is a BCM4313 802.11b/g/n and I run BackTrack 5 R1. I have found the drivers for my wireless controller and downloaded them. I have followed the README.txt until I encountered some problems/errors and didn't know what to do anymore, so I pray someone will have an answer for me :D

Here are the steps I've done:

```
# apt-get install build-essential linux-headers-generic
[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-headers-generic has no installation candidate[/I]

# apt-get build-dep linux
[I]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: You must put some 'source' URIs in your sources.list[/I]

# mkdir hybrid_w1

# cd hybrid_w1

# tar xzf /media/5C87-3B85/hybrid-portsrc_x86_32-v5_100_82_112.tar.gz

# make
[I]KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r` /build M=`pwd`
make: *** /lib/modules/2.6.39.4/build: No such file or directory.   Stop.
make: *** [all] Error 2[/I]
```
I am kind of desperate, I need help please.

Thank you for your time

nikkoN

---

### Post by Dandalf on 2011-12-17
Bump as I am in this exact same situation.

---

### Post by clever_fox on 2012-01-01
Hi try

root@bt:~# prepare-kernel-sources
root@bt:~# cd /usr/src/linux
root@bt:~# cp -rf include/generated/* include/linux/

---

