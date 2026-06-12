---
title: "apt-get update problem"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-03-27
[I]Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Err [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release.gpg
  Could not connect to mirror.ubuntulinux.nl:80 (82.148.208.151), connection timed out
Err [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Translation-en_US
  Could not connect to mirror.ubuntulinux.nl:80 (82.148.208.151), connection timed out
Err [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Translation-en_US
  Could not connect to mirror.ubuntulinux.nl:80 (82.148.208.151), connection timed out
Fetched 390kB in 6m2s (1077B/s)
Failed to fetch [http://mirror.ubuntulinux.nl/dists/edgy-seveas/Release.gpg](http://mirror.ubuntulinux.nl/dists/edgy-seveas/Release.gpg)  Could not connect to mirror.ubuntulinux.nl:80 (82.148.208.151), connection timed out
Failed to fetch [http://mirror.ubuntulinux.nl/dists/edgy-seveas/all/i18n/Translation-en_US.bz2](http://mirror.ubuntulinux.nl/dists/edgy-seveas/all/i18n/Translation-en_US.bz2)  Could not connect to mirror.ubuntulinux.nl:80 (82.148.208.151), connection timed out
Failed to fetch [http://mirror.ubuntulinux.nl/dists/edgy-seveas/all/i18n/Translation-en_US.bz2](http://mirror.ubuntulinux.nl/dists/edgy-seveas/all/i18n/Translation-en_US.bz2)  Could not connect to mirror.ubuntulinux.nl:80 (82.148.208.151), connection timed out
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/edgy/avant-window-navigator/binary-i386/Packages.bz2](http://download.tuxfamily.org/syzygy42/dists/edgy/avant-window-navigator/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: Duplicate sources.list entry [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Packages (/var/lib/apt/lists/mirror.ubuntulinux.nl_dists_edgy-seveas_all_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/avant-window-navigator Packages (/var/lib/apt/lists/download.tuxfamily.org_syzygy42_dists_edgy_avant-window-navigator_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I][B]

i tried to do apt-get update.. i got all this.. is there a problem.. if so, how can i fix it ?[/B]

---

### Post by HunkieChan on 2007-03-27
can anyone give me a solution ? please

---

### Post by h0ax on 2007-03-27
Looks like you have a source down and a duplicate source

you want to edit your sources.list

sudo gedit /etc/apt/sources.list

Find the one that is "mirror.ubuntulinux.nl" and put a # in front of the line (comment it out)
Then look for the duplicate one, and either delete that line or comment it out as well

---

### Post by DougieFresh4U on 2007-03-27
You can post your sources list and some can help you fix it if you are still having errors:)

---

### Post by HunkieChan on 2007-03-27
thanks bro

---

### Post by HunkieChan on 2007-03-27
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
# deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

## Debian Sarge (stable) users: 

## Debian Etch/Sid (testing/unstable) users: 
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev

deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator

---

### Post by HunkieChan on 2007-03-27
**im good.. i did the comment .. it doesnt show any error.. thank you guys..**

---

