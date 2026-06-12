---
title: "Synaptics or apt-get giving errors in /etc/apt/sources.list"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by keith11 on 2007-01-23
I am getting the following error when I click on the "reload" button in software sources window:

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

My network connection is fine, but I still get that error. The next window which follows the above error says the following:

"E: Malformed line 19 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory"

I am pasting my /etc/apt/sources.list:

"
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe #Added by software-properties

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

# Medibuntu multimedia packages
# GPG key: 0C5A2783
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# deb [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) edgy free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) edgy free non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse universe #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
#AUTOMATIX REPOS END
"

I was just following the commands on one of the posts about how to install the latest Mplayer and it codecs and after a few commands and executions I have been getting the above mentioned errors. How to solve this issue? Thanks.

---

### Post by meng on 2007-01-23
Look at line 19:
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
You would need to specify something else, like "main restricted universe multiverse"
BUT
you've already got this in line 3.
So just delete line 19 and be done with it!
(sudo nano -B /etc/apt/sources.list
make the edits and press ctrl-x to exit)

---

### Post by keith11 on 2007-01-23
Thanks for your prompt response. Just after posting this question I went back and edited line 19 and 20 as the following:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

Now I am able to parse the list of sources but I get the following error now:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I did update the repositories but I keep on getting the same error. How to get rid of it?
Thanks.

---

### Post by meng on 2007-01-23
You already have these in lines 3 and 4. That's why the duplicate alert.

---

### Post by Bachstelze on 2007-01-23
That's because you have edgy/universe twice, on lines 3 and 19. Just delete line 19 and you should be fine.

---

