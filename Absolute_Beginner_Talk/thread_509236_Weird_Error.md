---
title: "Weird Error"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by blithen on 2007-07-25
When I run synaptic package manager I get this error.

```
E: Malformed 3rd word in the Status line
E: Error occurred while processing liblzo1 (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```
I figured it would help if I upload the contents of my 'status' file so here it is.

---

### Post by blithen on 2007-07-25
Okay so I started working through my problem and I fixed the messed up word in the status file BUT I know get this error when I try going into synaptic and fixing the broken packages.
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to lock the download directory
```

---

### Post by blithen on 2007-07-25
I apologize, I shouldn't have posted this, I fixed the problem by using mousepad and correcting the few lines of the 'status' file that were corrupt.

---

