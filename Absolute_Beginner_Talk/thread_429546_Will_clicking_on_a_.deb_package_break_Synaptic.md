---
title: "Will clicking on a .deb package break Synaptic?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-05-01
Hi.

The Mondo backup software is essential to me.  Unfortunately, a recent release had a fatal bug ([http://www.mondorescue.org/](http://www.mondorescue.org/)) and it's the broken version that has found its way into the Feisty repository.  As documented on the Mondo website, backups made with this version will not restore (which is rather serious!!!)

My questions (apologies for how very basic these are)

1.  If I download the .deb version of the fixed program from the mondo website and click it, will that install the package?

2.  If I do this, since Synaptic won't know about it, am I in danger of confusing Synaptic or/and my Ubuntu installation?

3.  Is there any way to make the Ubuntu Gods aware of the problem?  I know it's not Ubuntu's fault, but if people depend on the Mondo from the repository and then find they can't recover their data, it's going to reflect quite badly on Ubuntu (IMO).

---

### Post by lamalex on 2007-05-01
well if you have the broken version uninstall it, then install your .deb. nothing will break. The repo version will probably be updated soon. If it's a major bug like that I'd be shocked if that went unfixed.

---

### Post by whitefort on 2007-05-01
Many thanks - I'll give it a shot.

I think it *is* pretty serious, but as I say, the Ubuntu people can't be blamed.  It's totally shocking that the mondo creators ever let such a flawed version escape, though.  They fixed their version (and apologised!).  I hope the fixed version makes it into the repo soon.

Thanks again.

---

### Post by mcduck on 2007-05-01
> **whitefort said:**
> 
2.  If I do this, since Synaptic won't know about it, am I in danger of confusing Synaptic or/and my Ubuntu installation?

Synaptic will know about it. All Ubuntu/Debian package managers are, in the end, just nice frontends to dpkg which actually handles installing, removing and updating your packages. And they all use the same .deb packages.. :)

When you install any .deb package it will also appear in Synaptic and every other package management tool.

---

### Post by webjames on 2007-05-01
it might warn you about having an earlier version in the repos but ignore this and continue. synaptic will be fine. to remove it you can go the synaptic and search and it will appear just like if you'd installed it with synaptic.

brilliant hey?!

---

### Post by whitefort on 2007-05-01
Thanks, guys - the news about Synaptic is very welcome and will be helpful for future reference.

In the meantime, I'm trying to install the latest Mondo and am getting dependency problems...

Oh well, I guess this is just going to be another of those 'Learning Linux' experiences...  I'll keep trying.  But I really do need to get a Mondo working properly ASAP, or I'm going to have to switch back to Dapper until things get fixed.

Thanks again!

---

