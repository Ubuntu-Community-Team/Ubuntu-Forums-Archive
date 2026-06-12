---
title: "Newb In Distress"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Warren Peace on 2007-02-19
i'm currently running ubuntu 5.10 "breezy badger" on a Pentium II dell i386, cable hsi through a d-link router.

Problem: every time i'm trying to install in terminal i keep getting this message

  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Fetched 3B in 6s (0B/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

i'm not really sure what to do at this point i've been working on getting this to work for a couple of weeks now, but if anyone could point me in the right direction i'm sure i could figure it out

---

### Post by meng on 2007-02-19
Well I can't connect to that server either, so either it's down or it doesn't exist anymore. How did it come to be in your sources.list in the first place? Would you consider upgrading to Ubuntu 6.06, the current long-term support version of Ubuntu?

Please show the output of this command (in the terminal):

cat /etc/apt/sources.list

---

### Post by Warren Peace on 2007-02-19
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
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

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free


yes i would be willing to upgrade, i've tried several times but i can never get my network card/router to work with 6.06 or 6.10 its an xircom rem56g-100 ethernet/56k modem combo

---

### Post by meng on 2007-02-19
Ah well, then maybe you'd better stick with Breezy for now. Do this:

sudo nano -B /etc/apt/sources.list
(enter your user password when prompted)
and delete the last 7 lines (from ## PLF repositories, onwards)

then save (ctrl-x)

and:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Warren Peace on 2007-02-19
ok went in and deleted the 7 lines that you told me to, saved and went back in to the terminal and this is what happened

forsaken@forsaken:~$ sudo apt-get update
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Fetched 3B in 2s (1B/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
forsaken@forsaken:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
forsaken@forsaken:~$

---

### Post by meng on 2007-02-19
Are you sure you saved the changes?

cat /etc/apt/sources.list

again please.

---

### Post by Warren Peace on 2007-02-20
ah yes! that worked, thanks for all your help and patients

---

