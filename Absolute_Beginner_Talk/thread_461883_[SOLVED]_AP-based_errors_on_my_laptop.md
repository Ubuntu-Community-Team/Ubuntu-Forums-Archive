---
title: "[SOLVED] AP-based errors on my laptop"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by waggygee on 2007-06-02
Recently I installed Ubuntu 7.04(feisty fawn) on my Acer laptop (Intel core Duo processor 1.66GHz, 1GB DDR2, 120GB HDD). I installed it usin the same CD I used to install Ubuntu on my desktop computer. After installing, booting and shutting down on the laptop takes a little longer than it does on the desktop computer and when I attemt to install apps (using Synaptic package manager, add/remove applications or automatix) I receive a error message that reads:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

or I receive this:

apt-based error occurred and installation was unsuccessful

I do have a working internet connection and I did not alter any preferences. When I installed it on the desktop computer I had the same problem but this was fixed after downloading the latest update.Updating worked with the laptop but the problem was not solved (as on the desktop computer)

---

### Post by ajmorris on 2007-06-02
> **waggygee said:**
> Recently I installed Ubuntu 7.04(feisty fawn) on my Acer laptop (Intel core Duo processor 1.66GHz, 1GB DDR2, 120GB HDD). I installed it usin the same CD I used to install Ubuntu on my desktop computer. After installing, booting and shutting down on the laptop takes a little longer than it does on the desktop computer and when I attemt to install apps (using Synaptic package manager, add/remove applications or automatix) I receive a error message that reads:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

or I receive this:

apt-based error occurred and installation was unsuccessful

I do have a working internet connection and I did not alter any preferences. When I installed it on the desktop computer I had the same problem but this was fixed after downloading the latest update.Updating worked with the laptop but the problem was not solved (as on the desktop computer)


can you please post your /etc/apt/sources.list file.

---

### Post by waggygee on 2007-06-02
Is this the right one?

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://bw.archive.ubuntu.com/ubuntu/](http://bw.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe

---

### Post by ajmorris on 2007-06-02
try commenting out the Automatix repos.

i.e. replace all these: 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

with these:

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

---

### Post by waggygee on 2007-06-03
I think I posted the source list from the computer that doesnt have problems, I apologise for this. This is the source.list file on the laptop:

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

Im sorry for the mistake. I notice that this source.list says some stuff about breezy badger but let me point out that I am running feisty fawn and not breezy badger (I used the same ubuntu7.04 feisty fawn cd that I used to install ubuntu on my desktop computer)

---

### Post by quinnten83 on 2007-06-03
try copying your feisty sources.list from your desktop to your laptop.
you can make a backup of the current sources.list just in case.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
sudo gedit /etc/apt/sources.list
copy the contents that you pasted on the forum to the gedit window.
save and then 
sudo apt-get update

I think you should be good to go..

---

### Post by waggygee on 2007-06-03
I copied the feisty fawn source.list and updated as instructed, everything ran smoothly untill this showed at the end:

99% [53 Packages gzip 0] [Waiting for headers]                      24.8kB/s 0s
gzip: stdin: not in gzip format
Err [http://bw.archive.ubuntu.com](http://bw.archive.ubuntu.com) feisty/universe Packages                      
  Sub-process gzip returned an error code (1)
Get:54 [http://bw.archive.ubuntu.com](http://bw.archive.ubuntu.com) feisty/universe Packages [4912kB]          
99% [54 Packages gzip 0]                                            24.8kB/s 0s
gzip: stdin: not in gzip format
Err [http://bw.archive.ubuntu.com](http://bw.archive.ubuntu.com) feisty/universe Packages                      
  Sub-process gzip returned an error code (1)
Fetched 3083kB in 1m59s (25.9kB/s)                                             
Failed to fetch [http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://bw.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by waggygee on 2007-08-02
It eventualy worked.... Im not sure what I did to get it running... It just worked on time

---

