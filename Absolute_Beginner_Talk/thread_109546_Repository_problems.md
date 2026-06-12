---
title: "Repository problems"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by ImplicitProcrastination on 2005-12-28
Hopefully this won't be as stupid of question as the last one posted.

I have some serious repository problems.

Automatix played with them, then I left college for break where I now access the internet through my uncle's wireless router, which uses a cable modem,  instead of the Ethernet connection on my college's network.

Ever since I got down here my repositories simply dont work, not the ones put in my default only, not the ones from the automatically genereated ones at that website, not other peoples, not automatix's... can't figure out what the problems are, I always get error messages similar to this: 

[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)

followed immediately by:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


for a while I couldn't even get the internet or my email to work, somehow I managed to fix that by messing with it.

Help?

---

### Post by darth_vector on 2005-12-28
make sure your internet is working and follow the instructions here:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by ImplicitProcrastination on 2005-12-28
I've done this now, nothing. I know my internet is working because I can get on this website, check my email, and use gAIM.

this is my output:


rockstar@notCancer:~$ sudo apt-get update
Reading package lists... Done
rockstar@notCancer:~$ sudo gedit /etc/apt/sources.list
rockstar@notCancer:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  Cannot initiate the connection to archive.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Cannot initiate the connection to security.ubuntu.com:80 (0.0.32.144). - connect (22 Invalid argument)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

its almost as if for some reason only apt-get and synaptic cant access the internet

---

### Post by d1337 on 2005-12-28
Could you post you /etc/apt/sources.list

d1337

---

### Post by ImplicitProcrastination on 2005-12-28
Well here it is right now, I've tried like fifty different ones.

##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
 ## Uncomment the following two lines to fetch updated software from the network
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by jimrz on 2005-12-28
pretty short list there. go [**[COLOR="Sienna"]here[/COLOR]**]("http://psychocats.net/linux/sources.php") for a good up to date list of ubuntu repository. It has good instructions for updating your sources list and the list itself, which you can copy/paste into your  system. I have this bookmarked since they seem keep it pretty well up to date.

---

### Post by ImplicitProcrastination on 2005-12-29
Thanks, I've tried this site's repository list, but nothing doing.

I think it might have something to do with my internet connection, because some sites, like amazon.com don't always come up (although sometimes they do, like just now), but others, like yahoo.com, this site, and my politics syllabus always do. My Kompete works, as does LimeWire, and everything else involving the internet, except for this...

Totally weird, but I really want to know if I need any updates as I'm sure i probably do. 

BAH!

---

### Post by spincricket on 2005-12-29
hum thats weird but this stuff is definately screwed up repositories:
```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Try again:
```
sudo gedit /etc/apt/sources.list
```
Delete the contents and paste this:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```
SAVE, close. then:
```
sudo apt-get update
```

---

### Post by d1337 on 2005-12-29
I don't know why your sources.list looks funny to me...it just does.  But looking closely, I think that it's okay, just not as robust as others.

I think that this is linked to your internet connection problem.  If I unplug my ethernet and try apt-get update, I get similar errors.  In post #3, Ign typically means it's hitting.  Maybe you connection is choppy?  I would tackle internet first, then lets look at your repos (if your connection doesn't fix the issue).

Maybe your wireless isn't getting a good hook to the router?  Do you have access to an ethernet connection that you could try out?

d1337

---

### Post by ImplicitProcrastination on 2005-12-30
Well, as I was messing with it, just trying to get the internet to work, I tried plugging a cord in through the back of the router.

Same result as wireless, but after a couple of annoying hours of going in circles I finally got it to work with the wireless. Maybe now that the wireless works I will be able to get the Ethernet cord to work as well and that will solve the problem. I'll try repasting again (and saving, which I always do) as spincricket suggested, and try to get it to work with the Ethernet cord.

A double click on my connection thingy in the panel reveals that my signal strength is 95 percent, for what that's worth.

How on earth do I build a robust list? Automatix gave me something of a robust one, but I tore it all to pieces trying to get it just work in general.

I'll take another lap around the track, implementing these suggestions and report back to you guys.

Thanks again...

---

### Post by Suger on 2005-12-30
Check in network-admin (System/Administration/Network) that you have the right  gateway interface (that you are using the wireless one and not the ethernet one).

And do you have a proxy ?

---

### Post by ImplicitProcrastination on 2005-12-30
Well copying and pasting the previously suggested one didn't work with the wireless. I have yet to break out the Ethernet cord, will get around to that. I don't have a proxy, to my knowledge. System/Administration/Networking's default gateway device is set to athos, which is the proper one isn't it?

Also, I've found that firefox doesn't display most websites anymore, for possibly the same reasons that synaptic and apt-get aren't connecting... but konqueror and email and limewire work fine. The solution to this problem is probably so easy that I'm gonna kick my own ass...

---

### Post by ImplicitProcrastination on 2005-12-31
So far, I still haven't played with the ethernet cord (got to dig it out, trying to fix computer in between other obligations).

To make matters worse I uninstalled synaptic using apt-get to see if that might help if i reinstalled it, but I hadn't counted on apt-get and aptitude not being able to connect at all (thus I'm now without synaptic and really close to just backing up my data and reformatting my hard drive, I fear though, that if I do that, the same thing that is happening to me now will happen in reverse when I go back to college). So now I'm trying to figure out how to fix that... which wouldn't be too hard if apt-get would make a connection. Doh.

I suspect the problem has something to do with my connection... I'm about to go digging through the wiki and these forums to see if something involving roadrunner might now be causing the problems. It seems like websites decide to load randomly when they feel like. Google is the only one that works consistetly, other websites, such as yahoo, this website, amazon.com and howstuffworks.com work when they feel like it... which I find too weird.

I'm still open to suggestions, although hesitant to use the ethernet cord because the last time I tried to get it work on this connection resulted in a step backwards but hey, thats probably me... I think I've fucked shit up to the point where I can experiment a little and pray this works... but only after I've finished this paper...

bah... I hate doing papers on an imperfect system...

An a completely unrelated tangent, Linux kicks ass, Ubuntu kicks ass, all of you wonderful people who are here willing to donate your time to help other people figure all this out kickass, and someday I hope to be smart enough to contribute something to the development of this fine operating system, which despite the troubles I'm having, has already trumped windows in the amount of time it has consistently served me without causing any problems. So for all of that you guys all kick alot of ass. Sorry about the run-on.

---

### Post by ImplicitProcrastination on 2006-01-07
hi everyone I'm back.

I've now exhausted everything I know to do. I've tried it corded, corded through the router, wirelessly, formatting the hard drive and reinstalling ubuntu, contacting roadrunner for help. Wow...

I have no idea, I'm not behind a proxy.

---

### Post by JimmyBEng on 2006-01-07
just a guess but it seems like the problem is more with the router setup or the isp.  is there some kind of firewall enabled on the router?  are there other computers on the same router, what kinds of problems do they have with internet apps? just some other ideas to help diagnose the problem

---

### Post by psyone on 2006-01-07
hi

I pretty much have the same problem. When I use apt-get I get this:

(it's in dutch..)

```
stef@laptopStef:~$ sudo apt-get update
Ophalen:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ophalen:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Ophalen:3 http://security.ubuntu.com breezy-security Release [19,6kB]
Ophalen:4 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Ophalen:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Geraakt http://security.ubuntu.com breezy-security/main Packages
Ophalen:6 http://archive.ubuntu.com breezy Release [30,9kB]
Geraakt http://security.ubuntu.com breezy-security/restricted Packages
Geraakt http://security.ubuntu.com breezy-security/main Sources
Ophalen:7 http://archive.ubuntu.com breezy-updates Release [19,6kB]
Geraakt http://security.ubuntu.com breezy-security/restricted Sources
Ophalen:8 http://archive.ubuntu.com breezy-backports Release [19,6kB]
Genegeerd http://archive.ubuntu.com breezy-backports Release
Geraakt http://security.ubuntu.com breezy-security/universe Packages
Genegeerd http://archive.ubuntu.com breezy/main Packages
Genegeerd http://archive.ubuntu.com breezy/restricted Packages
Geraakt http://security.ubuntu.com breezy-security/universe Sources
Genegeerd http://archive.ubuntu.com breezy/main Sources
Genegeerd http://archive.ubuntu.com breezy/restricted Sources
Ophalen:9 http://archive.ubuntu.com breezy/universe Packages [2304kB]
Genegeerd http://archive.ubuntu.com breezy/universe Packages
Ophalen:10 http://archive.ubuntu.com breezy/universe Sources [914kB]
Genegeerd http://archive.ubuntu.com breezy/universe Sources
Genegeerd http://archive.ubuntu.com breezy/multiverse Packages
Genegeerd http://archive.ubuntu.com breezy/multiverse Sources
Genegeerd http://archive.ubuntu.com breezy-updates/main Packages
Ophalen:11 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Genegeerd http://archive.ubuntu.com breezy-updates/restricted Packages
Ophalen:12 http://archive.ubuntu.com breezy-updates/main Sources [5088B]
Ophalen:13 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
2% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fout http://archive.ubuntu.com breezy-updates/restricted Sources
  Subproces bzip2 gaf de foutcode 2 terug
Ophalen:14 http://archive.ubuntu.com breezy-backports/main Packages [10,4kB]
2% [14 Packages bzip2 12288] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                             14,2kB/s 3m48s
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fout http://archive.ubuntu.com breezy-backports/main Packages
  Subproces bzip2 gaf de foutcode 2 terug
Ophalen:15 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
2% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                                                       14,2kB/s 3m48s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Fout http://archive.ubuntu.com breezy-backports/restricted Packages
  Subproces bzip2 gaf de foutcode 2 terug
Genegeerd http://archive.ubuntu.com breezy-backports/universe Packages
Genegeerd http://archive.ubuntu.com breezy-backports/multiverse Packages
Ophalen:16 http://archive.ubuntu.com breezy/main Packages [769kB]
Fout http://archive.ubuntu.com breezy/main Packages
  Fout bij het lezen van de server - read ([COLOR="Red"]104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80][/COLOR]
Ophalen:17 http://archive.ubuntu.com breezy/restricted Packages [4735B]
2% [17 Packages gzip 0] [Wachtend op de kopteksten]                                                                                           14,2kB/s 4m42s
gzip: stdin: not in gzip format
Fout http://archive.ubuntu.com breezy/restricted Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:18 http://archive.ubuntu.com breezy/main Sources [305kB]
Fout http://archive.ubuntu.com breezy/main Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80]
Fout http://archive.ubuntu.com breezy/restricted Sources
  416 Requested Range Not Satisfiable [IP: 82.211.81.182 80]
Ophalen:19 http://archive.ubuntu.com breezy/universe Packages [3028kB]
Fout http://archive.ubuntu.com breezy/universe Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80]
Ophalen:20 http://archive.ubuntu.com breezy/universe Sources [1223kB]
Fout http://archive.ubuntu.com breezy/universe Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80]
Ophalen:21 http://archive.ubuntu.com breezy/multiverse Packages [116kB]
Fout http://archive.ubuntu.com breezy/multiverse Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80]
Ophalen:22 http://archive.ubuntu.com breezy/multiverse Sources [58,0kB]
Fout http://archive.ubuntu.com breezy/multiverse Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80]
Ophalen:23 http://archive.ubuntu.com breezy-updates/main Packages [20,4kB]
1% [23 Packages gzip 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                                  78,6kB/s 1m51s
gzip: stdin: not in gzip format
Fout http://archive.ubuntu.com breezy-updates/main Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:24 http://archive.ubuntu.com breezy-updates/restricted Packages [20B]
Ophalen:25 http://archive.ubuntu.com breezy-backports/universe Packages [25,6kB]
1% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.182)]                                                                       78,6kB/s 1m51s
gzip: stdin: not in gzip format
Fout http://archive.ubuntu.com breezy-backports/universe Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:26 http://archive.ubuntu.com breezy-backports/multiverse Packages [1241B]
56,9kB opgehaald in 16s (3384B/s)
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz Subproces bzip2 gaf de foutcode 2 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz Subproces bzip2 gaf de foutcode 2 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz Subproces bzip2 gaf de foutcode 2 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz Fout bij het lezen van de server - read (1[COLOR="Red"]04 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80[/COLOR]] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz 416 Requested Range Not Satisfiable [IP: 82.211.81.182 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) [IP: 82.211.81.182 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Pakketlijsten worden ingelezen... Klaar
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.

```

I think the main problem is the marked line: it says:
"connection by partner is reconfigured, IP:..."

I'm pretty sure its a problem with my dhcp, I get internet through a network from my university, so it's kind of like being behind a very big router..

The funny thing is, that about three day ago, synaptic worked excellently, but then I formatted and reïnstalled ubuntu and never got synaptic to work.
(my internet configurations is the same as far as I know so I have no clue about what it could be, and I don't find a lot of info about this problem..)

---

### Post by akniss on 2006-01-07
[QUOTE=ImplicitProcrastination]
... some sites, like amazon.com don't always come up (although sometimes they do, like just now), but others, like yahoo.com, this site, and my politics syllabus always do. My Kompete works, as does LimeWire, and everything else involving the internet, except for this...
[/QUOTE]

It kind of sounds to me like you're dealing with two separate problems here.  Just out of curiosity, what kind of router do you use now when you're having the internet prolems with certain sites?

---

### Post by psyone on 2006-01-09
I found a solution:

It turns out it was in de sources.list, I changed all my http:// to [ftp://,](ftp://,) and that solved al the problems.

If you want to view my sources.list file, find the thread that says: apt-get update problem (are something like it) that I posted, it's there..

---

### Post by ImplicitProcrastination on 2006-01-09
hi guys sorry i havent been around for a while (causing multiple bumps on this thread).

My sources.list seems to be sufficient now, but thanks anyway.

Guy who said I was dealing with two seperate problems, your insight is astute, I realized that not too long ago as well. This seems to be a router problem now.

I'm using a Blitz G 108 Mbps BWA711 wireless router, which I can't get to work at all now. However by shutting down the computer, unplugging the roadrunner, and plugging it in directly, I can at least get the internet to work but the problem is that cuts my uncle off from the internet.

---

### Post by lindejos on 2006-01-09
Could this be a problem with the ports at the router?  
What port does apt-get use to connect to the internet?

Some routers block ports by default.

---

### Post by ImplicitProcrastination on 2006-01-09
This is logical, my Uncle suggested also that the problem may have something to do with ports, that might also explain why som pages where coming up wirelessly and some others weren't. 

If it is such a problem I don't even know how to go about starting to to troubleshoot.

---

### Post by ImplicitProcrastination on 2006-01-09
[QUOTE=JimmyBEng]just a guess but it seems like the problem is more with the router setup or the isp.  is there some kind of firewall enabled on the router?  are there other computers on the same router, what kinds of problems do they have with internet apps? just some other ideas to help diagnose the problem[/QUOTE]

My uncle uses XP with it, it works perfectly for him. I would assume that there's a firewall on the router since I gather that routers tend to do that and this one is relatively new.

---

### Post by gravediggers on 2006-01-09
Your problem bring back nightmarish memories of my owm problems a while ago. I was suffering a similar error message with apt-get, and also connection problems with firefox. Because I was using DHCP, the default DNS was the router address. My router does a DNS proxy OK 90% of the tine (eg, ping *domainname* works) but plays up for apt-get and firefox. Whatever is causing the problem I haven't yet fixed, but I got around it by prepending my ISP DNS addresses in /etc/dhcp3/dhclient.conf. Here is a link to the thread discussing it 
[Could not download all repository indexes ]("http://www.ubuntuforums.org/showthread.php?t=89247&page=2")
maybe that might help??

---

### Post by ImplicitProcrastination on 2006-01-09
I think this is going to help enormously, but how do I figure out what DNS servers, etc. to use?

---

### Post by gravediggers on 2006-01-09
Don't know -my ones are probably no use to you, but there are a heap of them out there!
eg, [The Public DNS Service]("http://soa.granitecanyon.com/")

just try a Google!

---

### Post by ImplicitProcrastination on 2006-01-09
Is this something RoadRunner can probably tell me to fill in? I'm not sure I even quite understand what these settings do...

---

### Post by gravediggers on 2006-01-09
Roadrunner is ISP???

They could give you the primary and secondary DNS IP's, and may be able to tell you where to put them, although you'd get better help in that repect on this forum. The temporary fix is just to put them first in /etc/resolv.conf 
like 
*nameserver 204.xxx.yyy.1*

then if that works you can make it permamant, but first see if that fixes it!

---

### Post by ImplicitProcrastination on 2006-01-09
Well RoadRunner went out of their way to be less than helpful.

I have no idea what to put in for these settings or how to figure it out. Now, I noticed that I do get one address under DNS servers (in network configuration) when I am connected directly to the surfboard, and it always starts with 65. Could this be it?

My god the solution to this problem is so close I can taste it...

---

### Post by ImplicitProcrastination on 2006-01-11
bump

apparently this is against roadrunner policy, because other people would be able to like park and use it or something...

but they implied that if that didn't really happen they didn't care


so...

to that extent has anybody had a nightmare like this with roadrunner and dealt with it?

---

### Post by SlackNerd on 2006-07-17
I've had the same problem on 2 Ubuntu Dapper boxes.  Changed all the http:// to ftp:// and voila!  working like a champ now.  Thanks to Sugar(?) for that wonderful insight.  Mucho gracias to all the dev's and others that have posted with help.  

Derek

---

