---
title: "[SOLVED] Adept problem in Kubuntu"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2008-02-28
I just put together a computer and loaded Kubuntu 7.10. Have been using Ubuntu on another computer for about a year but am brand new to Kubuntu. Right after the install I got updates with default repositories enabled. Got most of the way through the updates and then got a message that updates could not be completed. Since then, add/remove or an attempt to get restricted drivers returns this message:

Another process is using the packaging system database (probably some
other Adept application or apt-get or aptitude).

I did some searching of the forums and found some similar issues that suggested running the following command in terminal:

```
kdesu kate /etc/apt/sources.list
```

which output the following:
```
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy
main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted
universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main
restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Okay, now what, if anything do I do with this? It is a brand new installation so I have nothing to lose by re-installing, but I would just as soon fix what I've got. Any suggestions?

---

### Post by apothecaryaaron on 2008-02-28
Kubuntu did that to me as well recently. I ended up doing a restart and it fixed the package manager error. 
 
However, some of my stuff was fried (wireless being a big one), being my only computer at the time (I was moving), I did a fresh install to get running quickly, so I am of no help.

---

### Post by igknighted on 2008-02-28
> **apothecaryaaron said:**
> Kubuntu did that to me as well recently. I ended up doing a restart and it fixed the package manager error. 
 
However, some of my stuff was fried (wireless being a big one), being my only computer at the time (I was moving), I did a fresh install to get running quickly, so I am of no help.

The problem is sometimes adept doesn't configure things properly (like when they need your input it fails).  You simply need to remove the lockfile.  I forget where this is, but try searching the forum for "adept lock".  And you repo's are not commented out, don't worry.

---

### Post by apothecaryaaron on 2008-02-28
> **igknighted said:**
> And you repo's are not commented out, don't worry.
 
I at first thought they were, then I thought not, but now I'm not sure.  It looks like the security.ubuntu repos are commented.  Is that something to ignore, as in it will fix itself?  (So the OP can fix if needed, and in case it happens to me again)
 
And thanks for the tip on the lock file.  I would have taken a couple of days to search for the fix under normal circumstances, but I didn't feel like digging through the mess of moving to find a cat5e cable.  It was time to experiment with new stuff anyway...

---

### Post by igknighted on 2008-02-28
that's what i get for not scrolling down... there are some commented out.  I hate that "feature" of the new installer.  I never have internet during install, but do soon afterwards, and it just adds way more hassle to my life to go fix what it screwed up.

---

### Post by paydaydaddy on 2008-02-28
I think I have it fixed. The adept lock search suggestion led me to 

[http://ubuntuforums.org/showthread.php?t=348952&highlight=adept+lock](http://ubuntuforums.org/showthread.php?t=348952&highlight=adept+lock)

which I found hepful. Thanks for the quick response. I will mark this as solved.

---

