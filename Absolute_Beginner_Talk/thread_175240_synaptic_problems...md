---
title: "synaptic problems.."
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by stansz on 2006-05-13
When i open synaptic package manager..this is the "error" message i get?? im just wondering wats wrong and how to fix it ? 


W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by wbmj on 2006-05-13
The error message is telling you that Synaptic does not have a valid list of packages. The easyiest thing to do is open a terminal and type SUDO APT-GET AUTOCLEAN. Then type SUDO APT-GET UPDATE. This will clear your Synaptic log and reinstall a clean list of reference files

---

### Post by stansz on 2006-05-13
sweet..good stuff...

thnkx a lot...cheers

---

### Post by wbmj on 2006-05-13
You're welcome....good luck.

---

### Post by keheikev on 2006-05-13
I tried installling with synaptic a temperature monitor but no prog shows up on any of the menus libsensors3, sensor and librrd2 it lists for sensord the following [http://www.lm-sensors.nu](http://www.lm-sensors.nu) but firefox says its invalid is there a temperature monitor to monitor the temperature of the mobo soyo k7v amd 2100 :KS ?:KS

---

### Post by wbmj on 2006-05-13
Are you using Gnome or KDE?

---

### Post by keheikev on 2006-05-13
I am usint th Gnome desktop with Ubuntu 5.10.
Keheikev:KS 
good morning from the golden state California

---

