---
title: "OS X question"
date: 2007-05-10
forum: Apple Intel Users
---

### Post by unixdotseth on 2007-05-10
is OS X based on linux?

---

### Post by turbojugend_gr on 2007-05-10
Nope it is based on FreeBSD if my memory is ok. FreeBsd and BSD in general is like a Linux cousin distributed on an MIT license (of this I am a litl' bit uncertain). FreeBSD is also UNIX. for more info wikpedia.org.

Again not sure but BSD is an earlier Unix dirrivative than Linux (derrived from Minix)

---

### Post by unixdotseth on 2007-05-10
so is Linux based off  of Unix?

---

### Post by turbojugend_gr on 2007-05-10
Of course!

---

### Post by turbojugend_gr on 2007-05-10
Well actually to be accurate. Linux was based on Minix, which was a Unix derrivative, but at the moment Linux has progressed so far that it can't be at all true to say tha it is based on minix, Linux is based on Unix is the only accurate description at the moment, as far as I am concerned.

---

### Post by fearpi on 2007-05-10
Linux, however, was not created from UNIX itself - it was created to be a UNIX-like operating system.

---

### Post by fearpi on 2007-05-10
See, this is the problem with using a forum with such active users. :)

---

### Post by benanzo on 2007-05-10
Linux started out as a "Unix-like" (some call it a clone) OS.  It has since taken a life of it's own that makes it very much similar to Unix, but different at the same time.  From an admin point of view you can translate much of your knowledge between the two with minimal learning-curve.

OS X is different.  You will hear many people say "It's Unix (or FreeBSD) under the hood."  This is not true.  While there is code from FreeBSD in OS X, it is very much a different OS.  OS X is really a frankenstein of several different code bases including FreeBSD, Mach and NEXTSTEP all lying underneath Apple's proprietary UI.

This manner of code integration has made OS X a kernel dev's nightmare.  It is not nearly as cleanly implemented as something like FreeBSD's kernel or Solaris and especially not the Linux kernel.

Apple's OS developers have to work significantly harder than they should to implement new technologies because of all the juggling they have to do between these different layers.  I would suspect that Apple is currently devoting a significant amount of their kernel people to cleaning up the Mach layer and streamlining the whole kernel for OS 11.  (Perhaps that's what's taking so long for Leopard???)

---

### Post by turbojugend_gr on 2007-05-10
> **fearpi said:**
> See, this is the problem with using a forum with such active users. :)

:lolflag:

---

