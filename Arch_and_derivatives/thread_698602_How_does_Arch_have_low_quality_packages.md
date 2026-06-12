---
title: "How does Arch have low quality packages?"
date: 2008-02-16
forum: Arch and derivatives
---

### Post by eljoeb on 2008-02-16
I saw someone comment a couple of times that Arch has poor quality packages.  What does this mean?  I swear I remember reading somewhere that Arch used the most vanilla packages with nearly no distro specific packaging.  Why are these packages of low quality?

---

### Post by PurposeOfReason on 2008-02-16
Can you post where you read this. Arch has the newest packages available and can even be so new to being unstable if you'd like.

---

### Post by fwojciec on 2008-02-16
> **eljoeb said:**
> I saw someone comment a couple of times that Arch has poor quality packages.  What does this mean?  I swear I remember reading somewhere that Arch used the most vanilla packages with nearly no distro specific packaging.  Why are these packages of low quality?

There are always people out there who are all too happy to pass damning judgments on things they don't really know or understand well enough to judge.

---

### Post by eljoeb on 2008-02-16
Hmmm... not sure.  I've been using Arch for almost a year now, and am pretty happy with it.  I saw the comment and couldn't figure out why.  However, I couldn't find it again, so I'm taking this as a sign from the internet gods that I need to stop posting in the forums of a distro I don't use.  Either that or I'm drinking too early again.

---

### Post by bwtranch on 2008-02-16
> **fwojciec said:**
> There are always people out there who are all too happy to pass damning judgments on things they don't really know or understand well enough to judge.
That's really true fwo. Another thing I would like to point out is that the package is only as good as the source code, anyway. Look at Windows if you don't believe it.

---

### Post by K.Mandla on 2008-02-16
> **eljoeb said:**
> I saw someone comment a couple of times that Arch has poor quality packages.  What does this mean?  I swear I remember reading somewhere that Arch used the most vanilla packages with nearly no distro specific packaging.  Why are these packages of low quality?
This is the first time I've heard of this, and frankly it sounds a little FUDdy. (Is that a word? :) )

---

### Post by b9anders on 2008-02-18
first I've heard of it.

The only bad package experience I've had with Arch was Exaile which had trouble deciphering some characters in the tags of my music collection and consequently refused to import any of it.

It was ridiculously easy to grab a PKGBUILD and compile the latest version from source to correct it though. Imo, the package management and the ease with which one can install from source for what isn't in the repositories is one of Arch's greatest strengths.

---

### Post by Crooksey on 2008-02-18
Probably someone complaing about the fact that they are unpatched and vanilla.

Some people prefer patched packages, opposed to vanilla.

---

### Post by Tristam Green on 2008-02-18
> **K.Mandla said:**
> This is the first time I've heard of this, and frankly it sounds a little FUDdy. (Is that a word? :) )

Could re-coin "FUDdyduddy!"

+1

---

### Post by mivo on 2008-02-18
If people start to spread FUD about Arch, the distro is obviously becoming popular and mainstream! ;)

---

### Post by RedSquirrel on 2008-02-18
I think the package quality of Arch is high, e.g., the Arch devs dealt with that kernel bug very quickly.

Incidentally, firefox is one package that *is* patched. That is the reason it's called "Bon Echo". ;)

---

### Post by yabbadabbadont on 2008-02-18
I just wish that all the packages were updated as quickly for security issues.  Mplayer is still vulnerable and the patches to fix it were released almost a month ago.  Granted, it isn't a critical part of the system, but given its popularity, and the fact that it is in Extra, I would think that it would have been updated by now.  (I even bumped the bug by adding direct links to the patches that Mplayerhq released)  Which reminds me, I need to pull down the PKGBUILD and rebuild it myself with those patches...

---

### Post by RedSquirrel on 2008-02-18
> **yabbadabbadont said:**
> I just wish that all the packages were updated as quickly for security issues.  Mplayer is still vulnerable and the patches to fix it were released almost a month ago.  Granted, it isn't a critical part of the system, but given its popularity, and the fact that it is in Extra, I would think that it would have been updated by now.  (I even bumped the bug by adding direct links to the patches that Mplayerhq released)  Which reminds me, I need to pull down the PKGBUILD and rebuild it myself with those patches...
Good point. A month is a long time. I wonder how many packages are in that state...

---

### Post by yabbadabbadont on 2008-02-18
> **RedSquirrel said:**
> Good point. A month is a long time. I wonder how many packages are in that state...

Not only that, but the PKGBUILD in the official cvs for mplayer won't build due to an invalid URL in the source array.  It was easily fixed, but it made me wonder about the quaility of the tree.  I poked around a bit in the tree and decided that I would rather put gentoo back on my machine.  I'm booted on the liveDVD now.  (which is why I've been a bit slow in the games threads ;))

---

### Post by PurposeOfReason on 2008-02-18
I just got my first complaint when mpd was updated but a dependicy was forgotten. It was fixed quickly though.

---

### Post by yabbadabbadont on 2008-02-18
@RedSquirrel: Hey, if you stay on Arch, would you mind testing a PKGBUILD for me now and then.  I have a package in the AUR that I maintain.  "ca-certificates"  It tracks the Debian (and Ubuntu and Gentoo) package by the same name, and hasn't been updated by them since early last year, so I doubt that I would need to bug you anytime soon.

---

### Post by RedSquirrel on 2008-02-18
Sure, no problem.

---

### Post by yabbadabbadont on 2008-02-18
> **RedSquirrel said:**
> Sure, no problem.

Thank you.  I'm going offline for a while.  I have to rebuild gcc and python, and then build xorg and fluxbox.  Have fun in the word games without me.  :D

---

