---
title: "Update problem"
date: 2010-03-29
forum: Apple Hardware Users
---

### Post by anurse on 2010-03-29
Hi all,

Apologies for the newbie question (but I'm really a newbie). Can I ask: what does this mean 

Failed to fetch [http://ports.ubuntu.com/dists/karmic/Release](http://ports.ubuntu.com/dists/karmic/Release)  Unable to find expected entry  [http://ftp.usf.edu/pub/ubuntu//source/Sources](http://ftp.usf.edu/pub/ubuntu//source/Sources) in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

And, how do I fix it. 

I get it when I run the update manager

I'm using 9.10 PPC G5 Ubuntu.

Best
Andrew

---

### Post by linuxopjemac on 2010-03-29
can you post us your /etc/apt/sources.list file?
```
cat /etc/apt/sources.list
```

and then copy and paste it in this forum.

---

### Post by anurse on 2010-03-29
Yes,

Here they are:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic main restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic restricted universe [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) restrict hardy deb-src main multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

# deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security restricted main
# deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security universe
# deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security multiverse
# deb [http://ppa.launchpad.net/kubuntu-ppa/](http://ppa.launchpad.net/kubuntu-ppa/) karmic main
# deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) karmic main restricted multiverse universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic restrict
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic restricted deb-src [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) hardy restricted
# deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security restricted universe [http://ftp.usf.edu/pub/ubuntu/](http://ftp.usf.edu/pub/ubuntu/) restrict hardy deb-src main multiverse

---

### Post by linuxopjemac on 2010-03-29
it looks bad, especially with that hardy stuff in there on the same line with karmic.

If I were you, I'd replace that file with the one on my website and replace the wording "lucid" with "karmic". That's important, otherwise your whole system will upgrade to lucid. I would not do that yet.

[http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)

---

### Post by anurse on 2010-03-29
Worked like a charm. linuxopjemac: many thanks. Smooth update when I tested it out this evening.

---

### Post by linuxopjemac on 2010-03-30
You are welcome :)

---

