---
title: "installing umbrello from source: cant find X includes"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-02-19
I'm trying to install umbrello 1.5.61 from the source files (Yes, I know it's better to use the repository packages, but those are version 1.5.5, which is crashing a lot and I'm hoping the newer version will prove more stable).  I downloaded and extracted the package, but when I run ./configure I get the following message:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I don't have a clue what this means or how to fix it.  Can someone help me, please?

---

### Post by Bachstelze on 2007-02-19
```
sudo apt-get install xorg-dev
```

---

### Post by Ba66e77 on 2007-02-19
Thanks, Hymn, but what are those?  X relates to the X-server, which is the windowing system, right?  What's this package?

---

### Post by Maestro23 on 2007-02-19
> **Ba66e77 said:**
> Thanks, Hymn, but what are those?  X relates to the X-server, which is the windowing system, right?  What's this package?

It's a metapackage that provides the development libraries for the X.Org X Window System.

Look the package up in Synaptic for more definition is you need it.

---

