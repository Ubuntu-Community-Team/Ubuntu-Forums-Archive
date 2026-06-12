---
title: "Can a local folder be added as a repository?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-17
Hi,

I'm thinking to reinstall Ubuntu as I got a few things wrong the last time around. Thing is though that I've got quite a slow internet connection and I'm really not looking forward to downloading all the updates and other various packages all over again.

Since I've still got all these packages on my HDD I'm thinking to save them on a different partition and get them form there after I reinstall.

I know you can install ***deb*** packages with ***dpkg*** but I'd rather set the whole folder as a repository so that Ubuntu does everything automatically.

Please let me know if this is possible and if so, how to do it.

Thanks

---

### Post by rockfloyd on 2006-07-17
i personally don't think that'll work, just for the fact that repositories are web sites, but good luck man

---

### Post by barisurum on 2006-07-17
If you have the files on a CD, then you can add that CD as a repository in Synaptic. There is an option in the program menu. I didnt try to add a folder or partition as a Repo but it must be possible too.

---

### Post by PriceChild on 2006-07-17
Maybe if you copied your apt cache folder in var, it wouldn't have to redownload? Just a thought.

---

### Post by Jagot on 2006-07-17
[https://help.ubuntu.com/community/PersonalRepositories](https://help.ubuntu.com/community/PersonalRepositories)

---

### Post by kwaanens on 2006-07-17
Does not work here.
I get: 
```
$ update-mydebs
Unprocessed text from ./FrostWire-4.10.9-2.i586.deb control file; info:
Package: frostwire
Version: 4.9.11
Section: Networking
Priority: optional
Architecture: all
Essential: no
Depends:
Pre-Depends:
Recommends:
Suggests:
Installed-Size: 16386
Maintainer: Gubatron [gubatron@gmail.com]
Conflicts:
Replaces:
Provides: frostwire
Description: A Truly Free and Open Source Peer to Peer client
             for the Gnutella Network. It's core is based on
             LimeWire. Which needs the Sun Java Runtime Environment
             (minimum version tested is JRE 1.4+)
. / .

```

The Packages.gz file contains a file with zero content, and the directory where the script points to includes 4 more debs besides Frostwire, which I don't see referred to by the script output.

- Ketil

EDIT: BTW, I "ln -s"-ed ~/bin/update-mydebs to /usr/bin, but no matter how I run it, it gives the same output.

---

### Post by az on 2006-07-17
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

---

### Post by cendant on 2006-10-27
So, where can this "dpkg-scanpackages"? As in

dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

My Edgy Eft complains that such command does not exist.

---

### Post by ilGaspa on 2006-10-27
dpkg-scanpackages isn't installed by default, but you can find it in the package dpkg-dev in the ubuntu repositories ;)

Once installed your script should work :)

apt-get install dpkg-dev

if my memory is right

---

### Post by cendant on 2006-10-28
Found much easier way!

in Synaptic go to 

**File -> Add downloaded packages**

---

### Post by h.mehdi on 2006-12-31
> **Jagot said:**
> [https://help.ubuntu.com/community/PersonalRepositories](https://help.ubuntu.com/community/PersonalRepositories)

Hi,

I've read this howto and just used [http://.](http://.).. instead of file:/... , now when I want to install some packages apt can fetch some packages and can't fetch some others. this is an ex:

```
admin@remotepc:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  bind9-host cpio dnsutils firefox gzip libbind9-0 libdns21 libgnutls12
  libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libnspr4 libnss3
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 libwmf0.2-7 libxfont1
  libxine-main1 linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mozilla-thunderbird openssh-client openssh-server python2.4
  python2.4-minimal readahead ssh xinit xserver-xorg-core
35 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.0MB of archives.
After unpacking 242kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gzip libssl0.9.8 python2.4 python2.4-minimal cpio libgnutls12 libisc11
  libdns21 libisccc0 libisccfg1 libbind9-0 liblwres9 bind9-host dnsutils
  libkrb53 openssh-server openssh-client libnspr4 libnss3 firefox libtag1c2a
  libtagc0 libtheora0 libwmf0.2-7 libxfont1 libxine-main1 linux-386
  linux-image-2.6.15-26-386 linux-restricted-modules-common
  linux-restricted-modules-2.6.15-26-386 mozilla-thunderbird readahead xinit
  xserver-xorg-core ssh
Install these packages without verification [y/N]? Y
Err http://<ip> archives/ gzip 1.3.5-12ubuntu0.1
  404 Not Found
Err http://<ip> archives/ libssl0.9.8 0.9.8a-7ubuntu0.3
  404 Not Found
Err http://<ip> archives/ python2.4 2.4.3-0ubuntu6
  404 Not Found
Err http://<ip> archives/ python2.4-minimal 2.4.3-0ubuntu6
  404 Not Found
Err http://<ip> archives/ cpio 2.6-10ubuntu0.2
  404 Not Found
Err http://<ip> archives/ libgnutls12 1.2.9-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisc11 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libdns21 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisccc0 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisccfg1 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libbind9-0 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ liblwres9 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ bind9-host 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ dnsutils 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libkrb53 1.4.3-5ubuntu0.1
  404 Not Found
Err http://<ip> archives/ openssh-server 1:4.2p1-7ubuntu3.1
  404 Not Found
Err http://<ip> archives/ openssh-client 1:4.2p1-7ubuntu3.1
  404 Not Found
Err http://<ip> archives/ libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ libtag1c2a 1.4-4~dapper1
  404 Not Found
Err http://<ip> archives/ libtagc0 1.4-4~dapper1
  404 Not Found
Err http://<ip> archives/ libtheora0 0.0.0.alpha7-1ubuntu1~dapper1
  404 Not Found
Err http://<ip> archives/ libwmf0.2-7 0.2.8.3-3.1ubuntu0.1
  404 Not Found
Err http://<ip> archives/ libxfont1 1:1.0.0-0ubuntu3.2
  404 Not Found
Err http://<ip> archives/ libxine-main1 1.1.1+ubuntu2-7.3
  404 Not Found
Err http://<ip> archives/ linux-386 2.6.15.25
  404 Not Found
Err http://<ip> archives/ linux-image-2.6.15-26-386 2.6.15-26.47
  404 Not Found
Err http://<ip> archives/ linux-restricted-modules-common 2.6.15.11-5
  404 Not Found
Err http://<ip> archives/ linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
  404 Not Found
Err http://<ip> archives/ mozilla-thunderbird 1.5.0.7-0ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ readahead 1:0.20050517.0220-0ubuntu5~dapper1
  404 Not Found
Err http://<ip> archives/ xinit 1.0.1-0ubuntu3.1
  404 Not Found
Err http://<ip> archives/ xserver-xorg-core 1:1.0.2-0ubuntu10.4
  404 Not Found
Err http://<ip> archives/ ssh 1:4.2p1-7ubuntu3.1
  404 Not Found
Failed to fetch http://<ip>/./gzip_1.3.5-12ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb  404 Not Found
Failed to fetch http://<ip>/./python2.4_2.4.3-0ubuntu6_i386.deb  404 Not Found
Failed to fetch http://<ip>/./python2.4-minimal_2.4.3-0ubuntu6_i386.deb  404 Not Found
Failed to fetch http://<ip>/./cpio_2.6-10ubuntu0.2_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libgnutls12_1.2.9-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisc11_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libdns21_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisccc0_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisccfg1_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libbind9-0_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./liblwres9_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./bind9-host_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./dnsutils_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libkrb53_1.4.3-5ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./openssh-server_1%3a4.2p1-7ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./openssh-client_1%3a4.2p1-7ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libnspr4_2%3a1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libnss3_2%3a1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtag1c2a_1.4-4~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtagc0_1.4-4~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtheora0_0.0.0.alpha7-1ubuntu1~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libwmf0.2-7_0.2.8.3-3.1ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libxfont1_1%3a1.0.0-0ubuntu3.2_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libxine-main1_1.1.1+ubuntu2-7.3_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-386_2.6.15.25_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-restricted-modules-common_2.6.15.11-5_all.deb  404 Not Found
Failed to fetch http://<ip>/./linux-restricted-modules-2.6.15-26-386_2.6.15.11-4_i386.deb  404 Not Found
Failed to fetch http://<ip>/./mozilla-thunderbird_1.5.0.7-0ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./readahead_1%3a0.20050517.0220-0ubuntu5~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./xinit_1.0.1-0ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./xserver-xorg-core_1%3a1.0.2-0ubuntu10.4_i386.deb  404 Not Found
Failed to fetch http://<ip>/./ssh_1%3a4.2p1-7ubuntu3.1_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

