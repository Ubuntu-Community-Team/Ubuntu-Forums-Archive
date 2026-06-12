---
title: "frustrated"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ashgeo on 2007-08-07
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) 
I am new to ubuntu and in desperate need of help!  I have an old IBM 600E laptop and have installed Beezy 5.10 on it.  I Can't install anything newer as an error message comes up about the BIOS being too old!

I would like to install some new software through synaptic (or the termainal) but get error messages like below from Synaptic.  I assume that the links are all broken and have got no idea how to fix them....

breezy/main Packages 
(/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)



I also want to install the drivers for a D-Link wireless dongle and have no real idea of where to start. I've got it connected to the outside world via a USB LAN adapter which works perfectly......

Thanks in advance for any help anyone can give me.:(

---

### Post by dca on 2007-08-07
Hasn't Breezy gone into non-support?  Eighteen month cycle, that's two goes into ten???   So, it is a possibililty all the repos are re-routed to support newer vers of the OS...

---

### Post by Regel on 2007-08-07
I suggest you install Dapper or Feisty. Breezy is not supported anymore, and I doubt it has any working repositories.

---

### Post by bapoumba on 2007-08-07
Please look here:
[http://ubuntuforums.org/showpost.php?p=3026621&postcount=13]("http://ubuntuforums.org/showpost.php?p=3026621&postcount=13")

Breezy is no longer supported and packages removed from the mirrors.
If you wish, you can change your sources.list to get packages from old-releases.ubuntu.com.
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

---

