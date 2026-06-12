---
title: "Can't find ppc packages?"
date: 2005-04-26
forum: Apple PPC Users
---

### Post by braskob on 2005-04-26
Hi,
I've recently upgraded to Hoary, and I've just added the following lines to sources.list:
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

When I run 'sudo apt-get update' I get the following:
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407) unstable Release.gpg
Ign cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release powerpc (20050407) unstable Release
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release [1348B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Fetched 1352B in 3s (386B/s)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/Release](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release)  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/unstable/Release](ftp://ftp.nerim.net/debian-marillat/dists/unstable/Release)  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/Release](ftp://ftp.nerim.net/debian-marillat/dists/testing/Release)  Unable to find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Can someone tell me what I'm doing wrong here? Thanks!

---

### Post by DJ_Max on 2005-04-26
That repostitory doesn't have ppc binaries.  So you can't use those repos

---

