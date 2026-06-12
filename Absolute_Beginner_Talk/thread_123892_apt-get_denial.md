---
title: "apt-get denial"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-01-31
g'day,
got the following error message in terminal: -

jeremy@UBUNTU:~$ apt-get install w32codecs
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

then the following when i open synaptic:- 

  W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


Does this mean that downloading software is impossible due to repositories being updated?
Newbie needs it spelled out :mrgreen:

---

### Post by heimo on 2006-01-31
Try
```
sudo apt-get update
sudo apt-get install w32codecs

```

---

### Post by carverj on 2006-01-31
wow. problem solved in minutes. Gotta love this community!

---

### Post by nmsmith on 2006-02-01
I seem to try everyone else's advice and it doesn't work for me. What's going on?!

```
nick@thrymr:~$ sudo apt-get update
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/main Packages
Err http://gb.archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)

[COLOR="DarkGreen"]. . . dot dot dot . . .[/COLOR]

http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.182). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)

[COLOR="DarkGreen"]. . . dot dot dot . . .[/COLOR]

W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
nick@thrymr:~$
```

---

