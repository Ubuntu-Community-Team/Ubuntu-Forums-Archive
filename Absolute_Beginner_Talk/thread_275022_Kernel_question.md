---
title: "Kernel question"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2006-10-10
How long does it usually take for kernel.org to come out with a new version to it appearing in the Ubuntu software upgrade repository?

---

### Post by az on 2006-10-10
> **MakLeod said:**
> How long does it usually take for kernel.org to come out with a new version to it appearing in the Ubuntu software upgrade repository?

That's a good question.

Upstream development never stops.  Most of the releases from upstream (whether it is the kernel or any other piece of software) are not as stable as the ones you get with your disto.

That being said, there is a lot of work to do on the software before including it into the distro.  In Ubuntu's case, there is a release every six months;  about two months before release, there is a version freeze.  So, unless there is a really good reason to use a more current version and risk breaking everything that interacts with that piece of software, the version of any software that goes into Ubuntu is at least two months old when released - maybe older.

For something like the kernel, you probably will have some development going on on several versions simultaneously.  For example, if it is not viable for someone to use the most recent version of the kernel, but they relaly need a certain feature, they may put work into getting that feature to work in a slightly earlier version of the kernel.

So, to answer your question, it depends.  The kernel that will be released with Edgy is not the very most recent version from upstream, but will probably get a few security updates over the next few months.  It is possible that some new features can be added that were ot part of that kernel when Edgy released.

---

### Post by MakLeod on 2006-10-10
Interesting.  Thank you.

---

