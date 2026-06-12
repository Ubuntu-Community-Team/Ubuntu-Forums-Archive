---
title: "What ever happened to old-releases?"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by ristosu on 2008-04-29
I'm using 4.10 Warty. Some time ago I had to replace the references to archive.ubuntu.com with old-releases.ubuntu.com. Today I get 302 RD. Redirect, I assume.

Does anyone know, where to point to in /etc/apt/sources.list?

---

### Post by schauerlich on 2008-04-29
Why are you still on Warty? It hasn't been officially supported for a very long time. You'd be best upgrading to one of the more recent releases. If you don't want to be a Hardy early adopter, you can probably find a 7.10 Gutsy Gibbon .iso somewhere.

---

### Post by ristosu on 2008-04-29
Well, the whole PowerPC platform is not officially supported anymore... and, in this case, my computer is so old, an OldWorld Beige G3, and the whole installation procedure is not simple either on these Macs, so I would like to skip it as long as it's possible. My experience tells that it's often impossible to boot a newer kernel on older Macs.

---

### Post by schauerlich on 2008-04-29
PowerPC is supported:

[http://cdimage.ubuntu.com/ports/releases/7.10/release/](http://cdimage.ubuntu.com/ports/releases/7.10/release/)

You can install Xubuntu or download Fluxbox if you're worried about RAM.

---

### Post by stream303 on 2008-04-29
Old-world - that got my interest since I once had an old world running NetBSD.

I can understand wanting to avoid the pain, but maybe this will be inspiring - it seems that you can run all the way up to Edgy according to these links on the old-world stuff:  (how easy it is might be another matter. :)

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

[http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/](http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/)

[http://www.gifford.co.uk/~coredump/beigeg3.htm](http://www.gifford.co.uk/~coredump/beigeg3.htm)

Don't sweat the not-officially-supported deal.  It only means that you can't get paid support (past dapper which is still lts), and show-stopper bugs in ppc won't stop the builds from happening on the mainstream architectures.  Newer versions are still available, but not mentioned on the "official" download page, but are available via torrent or at the main repository in the "ports" sections.

I'd definitely back up your apt cache to a cd in case you want to reinstall Warty, now that the repos are hard to find for it....

At any rate, it is nice to see an old-world machine still being put to good use!

---

### Post by cyberdork33 on 2008-04-29
> **EDavidBurg said:**
> PowerPC is supported:
PPC is _not_ "supported", but install images are still available...

---

### Post by stream303 on 2008-04-30
> **cyberdork33 said:**
> PPC is _not_ "supported", but install images are still available...

You really got my goat going into semantics here. :)  Gotta' take a breath here. 

It *is supported* by a community of volunteers! If that were not true, then just what is Colin Watson doing working on trying to improve the installer for a G5 fan problem for the next spin, 8.04.1?

Your statement is true, yet ambiguous enough by not mentioning unofficial support that it does a disservice the Ubuntu ppc community, a community in which the reigns were handed off to, and not dropped.

Please, we need all the help we can get by being super-informative.

Let's put it this way - if you asked this question, I would never give you a pat answer like that.

---

### Post by ristosu on 2008-04-30
Thanks, all. Maybe I should give it a try...

---

### Post by cyberdork33 on 2008-04-30
> **stream303 said:**
> It *is supported* by a community of volunteers! 

Your statement is true, yet ambiguous enough by not mentioning unofficial support that it does a disservice the Ubuntu ppc community, a community in which the reigns were handed off to, and not dropped.
When people say supported, I generally think officially supported by canonical, which it is not... of course there is community support, or there would be nobody in these forums!

My apologies if my comment offended anyone.

---

### Post by stream303 on 2008-04-30
No offense taken.

Rest assured that if someone were to make a sweeping generalization that Intel-based macs were nothing but standard X86 boxes that only needs a few utilities to load, I'd be the first one to set the record straight, and send them here to read your exemplary posts on why this isn't true.

United we stand!

I understand Canonical's corporate decision regarding ppc, but anyone doing an internet search may often come only across the corporate statement, without knowing about the volunteer work that goes on behind the scenes, and maybe that's why I get a little hot under the collar.  My apologies for that.

---

