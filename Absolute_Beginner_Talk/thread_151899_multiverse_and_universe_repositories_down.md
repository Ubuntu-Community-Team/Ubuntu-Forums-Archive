---
title: "multiverse and universe repositories down?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by MST3Kakalina on 2006-03-28
Are the multiverse and universe repositories down?  I am trying to apt-get some things from them (VLC and w32codecs) but nothing doing. 

If they're not, then I will post my sources.list and my error messages here posthaste.

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=MST3Kakalina]Are the multiverse and universe repositories down?  I am trying to apt-get some things from them (VLC and w32codecs) but nothing doing. 

If they're not, then I will post my sources.list and my error messages here posthaste.[/QUOTE]
I just ran apt-get update and they are up. I'm not sure what your problem is though.

---

### Post by WelterPelter on 2006-03-28
I was having some trouble with them earlier today.

---

### Post by MST3Kakalina on 2006-03-28
Well, crap.

> 
root@hplap:/usr/lib/win32/all-20050412# apt-cache search VLC
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)


That is my error.  This is my sources.list file.

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

When I comment out universe and multiverse, everything's rainbows and kittens.  That's why I thought there were server-side issues going on.

Ah good, at least I'm not the only one.

---

### Post by aysiu on 2006-03-28
Literally, thirty seconds ago... ```
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://security.ubuntu.com breezy-security Release [27.0kB]
Get:6 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Get:8 http://security.ubuntu.com breezy-security/main Packages [44.4kB]
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Get:9 http://archive.ubuntu.com breezy-updates/main Packages [38.0kB]
Get:10 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:11 http://archive.ubuntu.com breezy-updates/main Sources [18.2kB]
Get:12 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:13 http://archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Get:14 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:15 http://archive.ubuntu.com breezy-backports/universe Packages [26.1kB]
Get:16 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:17 http://security.ubuntu.com breezy-security/main Sources [13.8kB]
Get:18 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:19 http://security.ubuntu.com breezy-security/universe Packages [31.1kB]
Get:20 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B]
Get:21 http://security.ubuntu.com breezy-security/universe Sources [5007B]
Fetched 276kB in 2s (93.2kB/s)
Reading package lists... Done
``` It's not a server-side issue.

---

### Post by MST3Kakalina on 2006-03-28
Commenting out breezy main restricted and breezy-updates main restricted seems to have done the trick for me.

---

### Post by Mustard on 2006-03-28
I didn't think w32codecs was in the repositories.  I installed mine from a .deb locally with dpkg.

---

