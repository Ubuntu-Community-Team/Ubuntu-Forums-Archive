---
title: "PPC Linux Apps With Darwin"
date: 2007-03-18
forum: Apple PPC Users
---

### Post by NotPhil on 2007-03-18
Does anyone know if you can install Linux applications on Darwin? I think BSD, Linux, Solaris, Darwin and other UNIX clones are supposed to be compatible with each other, but, well, you know how that goes. 

So, has anyone tried to install PPC packages from a Linux distro on a PPC Mac (which already has Darwin underneath it).

If you're wondering why I would want to try this, it's because of the hardware drivers. OS X/Darwin already has the proprietary drivers installed and working, but PPC Linux doesn't seem to have drivers for things like the NVIDIA video card.

I've heard of Fink, which does something similar to what I want, but when I looked through Fink's site, it appeared as though it didn't have all of the GNOME desktop available.

---

### Post by grazie on 2007-03-18
No knowledge myself, but I'd imagine there's more likely to be info on the gentoo or debian sites and forums.

---

### Post by fkdev on 2007-03-18
No, it won't work, Darwin doesn't have a compatability layer 
for linux binaries (ELF). 
You can use fink/macports(formerly darwinports)/gentoo portage for OSX
if you want to install your normal unix stuff 
(fink (and in fact all of these, i think) does have a mostly complete gnome, so i'm not sure what you want not in there?)
and, from personal experience, I can tell you that 
you should just use linux if you want unix stuff (gnome, etc.) for powerpc.
the stuff will be slower than it is on mac os x, and you'll
be stuck with old versions of everything. If you go pure darwin,
then you wouldn't have the drivers anyway.

---

### Post by NotPhil on 2007-03-18
> **fkdev said:**
> No, it won't work, Darwin doesn't have a compatability layer for linux binaries (ELF). ...Bummer. 

But this wouldn't be a problem with FreeBSD PPC, would it?

---

### Post by grazie on 2007-03-18
Unless you want a server I think theres's a lot missing from FreeBSD.

---

### Post by ssam on 2007-03-19
~99% of things should work on darwin if you recompile them.

---

