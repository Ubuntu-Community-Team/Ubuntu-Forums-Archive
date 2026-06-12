---
title: "Chrome on PowerBook G4"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by Carleas on 2010-05-01
I've recently installed 8.04 server on an old PowerBook G4, and I'm wondering if I can install Chrome on it.  The problem I keep running into that Chrome doesn't like the powerpc architecture.  It seems to look for a powerpc version when using apt-get update (I added "http://dl.google.com/linux/deb stable non-free main" to my repositories list); it "fails to fetch" from google.
I also tried downloading a 32-bit .deb file from google and using dpkg, but it complains that the package architectures don't match.

I'm new to Linux, so I'm not sure how to get around this.

I'm also not sure that I can even run a browser on the server version of Hardy.  I don't see why not, but there's a lot I don't see 8-[

---

### Post by Dukenukemx on 2010-05-02
Don't think Chrome works on PPC, but I'm not entirely sure.  I was looking to see if Chrome worked on PPC Linux as well, but so far all signs point to no. 

There is a very negative reaction for Ubuntu to support PPC.  So nearly nobody cares enough to support those who still hold onto their G3,G4, or G5 machines.

---

### Post by clesenne on 2010-06-09
> There is a very negative reaction for Ubuntu to support PPC.  So nearly  nobody cares enough to support those who still hold onto their G3,G4, or  G5 machines.This is not strictly an Ubuntu problem. The [V8 JavaScript engine]("http://code.google.com/p/v8/") can't be built for ppc architectures at present. The same problem exists for [ppc on Mac OS X]("http://code.google.com/p/chromium/wiki/MacBuildInstructions"). [Blame Google]("http://www.google.com/support/forum/p/Chrome/thread?tid=5e2ea79f91d38cb4&hl=en"), or even better, submit a patch to get V8 compiled on powerpc.

---

