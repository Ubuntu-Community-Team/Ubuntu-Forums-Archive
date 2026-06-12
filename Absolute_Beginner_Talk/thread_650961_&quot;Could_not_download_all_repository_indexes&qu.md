---
title: "&quot;Could not download all repository indexes&quot;"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-12-27
Hi,

I'm getting an error that Gutsy can't downloaad all repository indexes. This is the specific address:

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  restrictedgksudo/source/Sources in Meta-index file (malformed Release file?)

What's up with that?

I just upgraded to gutsy on my laptap...my wireless did not automatically connect so gutsy commented out all the sources.  I went to the sources.list and uncommented all debs.  Now I'm worried I messed up my sources list.  Can someone tell me if my sources.list is ok - here is the code:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restrictedgksudo gedit /etc/apt/sources.list

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may nohttp://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release: Unable to find expected entry  restrictedgksudo/source/Sources in Meta-index file (malformed Release file?)t be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILLsudo apt-get update NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by tepidarium on 2007-12-27
Hi,

I think I messed up my entire sources.list by copying and pasting the wrong thing. Can someone post what the document should look like?

Why does ubuntu automatically comment out these sources if it initially can't get an internet connection!?

---

### Post by Kingsley on 2007-12-27
All but the first line look good to me. Try commenting it out. I'm talking about " deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted"

---

### Post by tepidarium on 2007-12-27
Thanks for your reply. Do you have that line commented out?

---

### Post by Kingsley on 2007-12-27
Yes, I have it commented. I never install programs from the Ubuntu CD.

---

### Post by tepidarium on 2007-12-27
It's enabled by default for me. Is this commented out from the get go for most users?

---

### Post by shawn.mnb on 2008-01-05
Hi,

Im getting the same error from my update manager. It says could not download all repository indexes and then:

[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

Im not sure what to do at this point. It mentions that I should look in preferences for the correct writing of the repository addresses. Which preferences should I be looking in? What more information is needed?

Hopefully you guy can help me out! Do you need more information?

---

### Post by kleo skywalker on 2008-01-05
Solved [here]("http://ubuntuforums.org/showthread.php?t=621059").
(The other things didn't work for me, so I just regenerated my source list.)

---

