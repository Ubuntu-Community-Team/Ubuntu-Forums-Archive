---
title: "apt-get update problem"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by asingh on 2006-03-30
Friends,
I am absolutely new to Ubuntu. I got the ubuntu 5.10 cd by ship-it from canonical. Installed it on my compaq P-4 system. It works perfectly Ok as to internet, printing to network printers, file sharing etc. I would like to install tetex (with kile) and some other scientific softwares. Following the advice in [http://ubuntuguide.org/ubuntu5.04.tar.gz](http://ubuntuguide.org/ubuntu5.04.tar.gz)
I edited the /etc/apt/sources.list and gave the command 
sudo apt-get update
I get the following message:
---------------------------------------------
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed out
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg)  Could not connect to ubuntu-backports.mirrormax.net:80 (72.232.67.226), connection timed out
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg)  Could not connect to ubuntu-backports.mirrormax.net:80 (72.232.67.226), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
--------------------------------
How do I fix it?
Thanks in advance.

[email]--arindamsingh@gmail.com[/email]

---

### Post by Kapre on 2006-03-30
asingh - your using the old sources list. You installed breezy and you should have breezy ports. Try this [site]("http://makuchaku.info/amnesty/#extrarepositories") (thanks to Aysiu)

---

