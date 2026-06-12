---
title: "Songbird for PPC"
date: 2008-12-14
forum: Apple Hardware Users
---

### Post by casbahdk on 2008-12-14
Unfortunately, there doesn't seem to be a PPC version of Songbird. I have noticed that there are Fedora RPMs for both 32 and 64bit PPC, as well as source code at this url:

[http://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds]("http://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds")

Which method would be the recommended way to get Songbird on my system - converting an RPM with Alien of building from source?

Cheers

---

### Post by eraker on 2008-12-14
I'm confused. Did you find a ppc-specific rpm that you want to convert with alien? If so and there's no ppc-specific .deb available, this is probably the best way to go.

If what you found is an i386 rpm, I'd just try to build the thing from source, first. Converting an RPM for i386 with alien would be like adding a step to just building it from source and it would be unlikely to work, I think.

I'm not sure if that helps at all.

---

### Post by casbahdk on 2008-12-14
There is no ppc specific .deb listed at the URL and there doesn't seem to be anything available from Synaptic. If I convert the .rpm, should I use the --script variable and with what syntax?

Cheers

---

### Post by Tim Sharitt on 2008-12-14
Your best bet is probably going to be to build it from source.

---

### Post by cyberdork33 on 2008-12-15
> **Tim Sharitt said:**
> Your best bet is probably going to be to build it from source.

+1
You could even make a .deb package directly from source with something like debuild or even checkinstall.

You might also let the folks [here]("http://www.ppclinux.info/") know, and they can host a deb in their PPA.

---

### Post by trentscott4 on 2008-12-15
> **cyberdork33 said:**
> +1
You could even make a .deb package directly from source with something like debuild or even checkinstall.

You might also let the folks [here]("http://www.ppclinux.info/") know, and they can host a deb in their PPA.

+2 Worked for me!

---

