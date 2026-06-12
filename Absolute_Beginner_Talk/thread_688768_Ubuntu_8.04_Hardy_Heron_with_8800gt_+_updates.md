---
title: "Ubuntu 8.04 Hardy Heron with 8800gt + updates"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by DeltaUK on 2008-02-05
Hey, i was wonderin, as im about to install ubuntu on my pc with an 8800gt

will hardy heron 8.04 contain the drivers for the 8800gt on the live cd so i can boot from it?

also if i use this alpha release, will i be able to update it to the full release from inside the OS using online updates?

Thx

---

### Post by overdrank on 2008-02-05
> **DeltaUK said:**
> Hey, i was wonderin, as im about to install ubuntu on my pc with an 8800gt

will hardy heron 8.04 contain the drivers for the 8800gt on the live cd so i can boot from it?

also if i use this alpha release, will i be able to update it to the full release from inside the OS using online updates?

Thx

Hi and it should as it has worked with my nvidia cards but I am not using 8800. I would suggest sticking with gutsy or setting up another partition for hardy. And yes if you are running the alpha it will update to the latest version.

---

### Post by DeltaUK on 2008-02-05
if it will update the latest version why do u suggest setting up a seperate partition for hardy?

---

### Post by overdrank on 2008-02-05
> **DeltaUK said:**
> if it will update the latest version why do u suggest setting up a seperate partition for hardy?

For the simple reason hardy is alpha and I would not recommended it as the primary OS'. It can still break.

---

### Post by Bothered on 2008-02-05
If you use hardy you should expect problems. For example, hardy has a new I/O abstraction layer that may not be completely stable (see [http://arstechnica.com/news.ars/post/20080202-first-look-ubuntu-8-04-hardy-heron-alpha-4.html](http://arstechnica.com/news.ars/post/20080202-first-look-ubuntu-8-04-hardy-heron-alpha-4.html)). One way of using the unstable ubuntu version is to install from an alpha CD, remove all update repositories from your /etc/apt/sources.list except for the CD, and then update from each successive alpha CD (although problems should still be expected!).

All in all, unless you like fixing your computer and have good backups it's recommended that you use the stable release.

---

### Post by DeltaUK on 2008-02-05
i use xp, i didnt think installing an unstable os on a different partition could have any effect on the xp partition?

---

### Post by rmockler on 2008-02-05
Just to pass my experience on to you - you are exactly right.  I tried Hardy alpha just for the fun of it,  and it turned out to be no fun at all.  I have progressed through four releases of Ubuntu, currently on Gutsy, and have had no major problems with final releases.  I tried Hardy too soon, and it was a disaster.  I expect that it will NOT be the case with the final release.  However, to confirm your last post, the whole fiasco had absolutely no effect whatsoever on my XP installation.  I was saved by having a good backup of my Gusty partition, and I pulled it back in and replaced the Hardy debacle successfully.  I will NEVER load a release prior to the final again.  
Hope this helps you out,
Richard

---

### Post by Moop on 2008-02-05
> **DeltaUK said:**
> i use xp, i didnt think installing an unstable os on a different partition could have any effect on the xp partition?

Normally it wouldn't but anything can happen with alpha software and there are posts in the hardy forum about people losing every partition on every hard drive when installing Hardy alpha 4. 

Be very careful. Heed the warnings.

---

### Post by DeltaUK on 2008-02-06
ok, but if i get gutsy can i update it to hardy from update manager when the full version is released?

---

### Post by jd65pl on 2008-02-06
> **DeltaUK said:**
> ok, but if i get gutsy can i update it to hardy from update manager when the full version is released?

Yes you will be able to do this

---

### Post by dondad on 2008-02-06
> **jd65pl said:**
> Yes you will be able to do this

You can do the upgrade, but sometimes there are problems that may cause you to need to do a fresh install. Set up your gutsy installation with a separate partition for /home so you can reinstall without losing your data. With the separate partition, a reinstall is not big deal, but without it, it is sometimes a mess. You should always have your data backed up, but it is nice not to have to reload it after a reload of the OS.

---

