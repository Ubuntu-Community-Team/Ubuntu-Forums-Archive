---
title: "Missing files - how to proceed?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by palmdoc on 2006-02-19
Lately when I launch the Synaptic package manager, it complains:

> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)


Could anyone explain how to troubleshoot missing files and how to reinstall?

TIA

---

### Post by Gimbo on 2006-02-19
I've been getting similar error messages. My assumption was that the repositories in question had moved or were temporarily down.

---

### Post by OBnascar on 2006-02-19
[QUOTE=palmdoc]Lately when I launch the Synaptic package manager, it complains:Could anyone explain how to troubleshoot missing files and how to reinstall?[/QUOTE]

You are connected to the internet, correct ? Have you tried inserting the ubuntu 5.10 breezy CD and then open the Synaptic package manager. I had the same thing happen a couple of months ago. It wasn't anything serious but I am not certain right now what I did for sure.

---

### Post by lha on 2006-02-20
Refresh package lists. Open Synaptic and click Refresh button or press <control>-R.

---

