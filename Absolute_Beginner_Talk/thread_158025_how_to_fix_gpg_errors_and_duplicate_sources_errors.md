---
title: "how to fix gpg errors and duplicate sources errors in package lists"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by sulien on 2006-04-10
when I perform apt-get update I receive these errors:

> W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E8DDB29170188C3B
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

how do I correct that?

---

### Post by Darkriser on 2006-04-10
try configuring your sources.list file according to this thread:

[http://ubuntuforums.org/showthread.php?p=907271](http://ubuntuforums.org/showthread.php?p=907271)

---

