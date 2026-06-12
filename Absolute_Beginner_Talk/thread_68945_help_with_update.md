---
title: "help with update"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by majkmil on 2005-09-24
When i try to update in synaptic  get this error, or apt-get also.


W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)


i am I doing something wrong with my repositories? any help will be appreciated.

---

### Post by fordfan753 on 2005-09-24
Post your sources.list

---

### Post by John.Michael.Kane on 2005-09-24
sudo gedit /etc/apt/sources.list replace with what is posted,

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
``` 

Hope it helps

---

### Post by fordfan753 on 2005-09-24
Your problem is with backports and the Marillat repositories. Just comment out the backports and the ftp.nerim.net ones. The backports are a little unreliable, and I think you put too many options after them. And the Marillat repositories are designed more for Debian, and don't always work for Ubuntu. Then use apt-get update.

---

### Post by ThePainter on 2005-09-25
Hi,
I cant get the repository update either.
The Error I get is;

[http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:) Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz:) Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:) Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:) Could not connect to us.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]


My sources list is;

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


I tried changing my source list to the one adviced in the post above with the same error.

Any ideas ?

---

### Post by Xian on 2005-09-25
[QUOTE=ThePainter]I tried changing my source list to the one adviced in the post above with the same error.[/QUOTE]
The mirrors are down at this time.
It is not a localized issue.

---

### Post by ThePainter on 2005-09-25
Hi,
OK Thanks, Ill try again later.

---

### Post by majkmil on 2005-09-25
when the mirrors are down is that why i get this (   Could not open lock file /var/lib/dpkg/lock . does this have a thanksnything to do with repositories? thanks

---

