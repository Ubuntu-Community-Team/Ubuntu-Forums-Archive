---
title: "What's a clvm?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by sabresong on 2007-05-20
Hello.

I've been using Ubuntu for about six months now, and feel pretty comfortable with installing and removing software via the terminal, except for one thing:  For the past month I've been seeing an error when using the terminal to do pretty much anything involving packages.  The error is:

invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3


I have no idea what a clvm is, why it's on my system and why it's not working.  Everything I use is working just fine, but I'd really like to be able to think that my system is error-free, or, failing that, not feel like I'm possibly overlooking something that may eventually have my system go through some sort of spontaneous meltdown.

I've tried a number of suggestions related to this sort of error, including apt-get -f install, apt-get clean and trying to reinstall the mysterious clvm, and the same using aptitude, all ending in the same error I'm trying to get rid of.

Can someone help me figure this out?

---

### Post by wormser on 2007-05-20
I found this on the web.

"This package provides the clustering interface for lvm2, when used with Red Hat's "cman" cluster infrastructure. It allows logical volumes to be created on shared storage devices (eg Fibre Channel, or iSCSI)."

From [http://packages.debian.org/unstable/admin/clvm](http://packages.debian.org/unstable/admin/clvm)

Hope that helps.  I still looking stuff up on it.

---

### Post by sabresong on 2007-05-25
That information was helpful.  I tried uninstalling and reinstallng the cluster manager, butstill have thesame error.  In fact, clvm won't uninstall, reinstall or apparently do anything at all useful.

Sorry it's taken me 4 days to respond.  I've had problems with my wife's computer to deal with, and hers is more important at the moment.  (She needs it for online classes.)

---

