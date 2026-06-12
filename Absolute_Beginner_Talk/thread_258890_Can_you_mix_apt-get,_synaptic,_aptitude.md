---
title: "Can you mix apt-get, synaptic, aptitude?"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Bill_MI on 2006-09-16
The advantages of aptitude for uninstall are known.  Aptitude also removes all dependencies.  Great.  But...

If you've installed a big package with apt-get or synaptic... what danger exists to use aptitude as the uninstall for this package?  The database (repositories, installed base and dependencies) for all these is common, right?

I'm wondering if repositories were changed between install/uninstall if something may disconnect, but that may happen with ANY method, correct?

---

### Post by comppsyco on 2006-09-16
I think, but I don't know, that if you installed something with apt-get, uninstalling with aptitude won't uninstall all the orphan dependencies. I do, however, think that there is some kind of "orphan" command within aptitude that will get rid of orphans. Try "man aptitude" to learn more.

---

### Post by bulldog on 2006-09-16
You can use them all together with no problem.

But as far as I know aptitude can't remove the dependency's you installed with apt-get,only the ones which are installed with aptitude.

That's why I only use aptitude.

---

### Post by Bill_MI on 2006-09-16
> **comppsyco said:**
> I do, however, think that there is some kind of "orphan" command within aptitude that will get rid of orphans. Try "man aptitude" to learn more.I see **--purge-unused** which sounds like an orphan handler.  I saw this before and STILL trying to form a commandline using this to view all such packages. ](*,)

---

### Post by oss_monkey on 2006-09-16
I think the command you're looking for is **deborphan**. It searches for packages that are orphaned in your system, but there have been reports that it identifies the gstreamer package as orphaned, even when Xmedia (if I remember correctly) uses it. Use with caution. :)

---

### Post by mlind on 2006-09-16
> **Bill_MI said:**
> I see **--purge-unused** which sounds like an orphan handler.  I saw this before and STILL trying to form a commandline using this to view all such packages. ](*,)

deborphan and debfoster

---

### Post by mlind on 2006-09-16
> **oss_monkey said:**
> I think the command you're looking for is **deborphan**. It searches for packages that are orphaned in your system, but there have been reports that it identifies the gstreamer package as orphaned, even when Xmedia (if I remember correctly) uses it. Use with caution. :)

That's normal though. If you look at deboprhan's description
> 
deborphan  finds  packages that have no packages depending on them. The
default operation is to search only within the libs and oldlibs sections to
hunt down unused libraries.

For instance, gstreamer0.10-plugins-ugly-multiverse is a package that no other package depends on and is considered as orphaned.

---

### Post by Bill_MI on 2006-09-17
Wow, deborphan itself depends on 4 packages - only one I didn't have installed was dialog.

On my system, deborphan identifies (3) gstreamer-plugins-xxxx and (1) libgtk1.2.  Hardly worth uninstalling if it isn't used.

If I removed libgtk1.2 and keep deborphan and dialog, I actually did negative work by package count. :lol:

---

