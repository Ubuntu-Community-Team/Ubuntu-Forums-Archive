---
title: "Asus N53SV cannot install update for xserver-xorg-video-openchrome"
date: 2012-04-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Dessel on 2012-04-09
I am running 11.10 and I can't get the update for xserver-xorg-video-openchrome to install because it has a dependency for xorg-video-abi-10 which I can't figure out how to fix. When I try to install it from terminal I get this:

 xorg-video-abi-10 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-video-abi-10 is a virtual package provided by:
  xserver-xorg-core 2:1.10.4-1ubuntu4.1 [Not candidate version]
  xserver-xorg-core 2:1.10.4-1ubuntu4.2 [Not candidate version]
  xserver-xorg-core 2:1.10.4-1ubuntu4 [Not candidate version]

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Package 'xorg-video-abi-10' has no installation candidate

and for xserver-xorg-video-openchrome

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-openchrome : Depends: xorg-video-abi-10
E: Unable to correct problems, you have held broken packages.

Ideas on how to fix this would be much appreciated.

---

