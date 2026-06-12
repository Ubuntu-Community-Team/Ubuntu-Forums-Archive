---
title: "Why do i get this with apt-get update?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-11-20
charles@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary ReleaseIgn cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  404 Not Found
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 4B in 12s (0B/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
charles@ubuntu:~$

How do i correct it, i get this you may want to run apt-get update everytime i open synaptic,i have run apt-get update but still get the message

---

### Post by aysiu on 2005-11-20
See my sig.

---

