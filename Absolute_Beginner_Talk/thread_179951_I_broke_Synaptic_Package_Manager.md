---
title: "I broke Synaptic Package Manager"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Michiba on 2006-05-21
Hello all,

I have used Ubuntu since January this year. I 've been getting braver and with the help of the forums been doing Ok. Not a power user, but ok. Now I have broken something. When I start the Synaptic Package Manager, I get the following:-

Warning

The following problems were found on your system.


W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)


What have I done? Is it terminal? Should I reinstall Breezy or wait till Dapper and upgrade.

Thanks
Michiba:-k

---

### Post by Jussi Kukkonen on 2006-05-21
Heh, don't go reinstalling anything -- those are not problems with your system actually, Synaptic just couldn't find the package lists it was looking for. The server was probably down at the time, or your internet connection had a problem. Just try again later.

---

### Post by macdo on 2006-05-21
Try running, in a terminal, ```
sudo apt-get update
```
(Make sure Synaptic is shut, first.)

---

### Post by argie on 2006-05-21
Strangely, that keeps happening to me every time I start Synaptic, and it's existed since I installed Ubuntu though my connection is quite obviously working.
I just click the Reload button and it manages to connect to the server this time. Probably a unique situation for me. I use a proxy to connect.

---

