---
title: "what the HECK does this mean?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by twizitid on 2006-02-12
what the HECK does this mean and what do i do to fix it?

configure: error: conditional "HAVE_ORBIT" was never defined.
Usually this means the macro was only invoked conditionally.

this happened when trying to compile Drip, yes i tried Synaptic, something gets botched with synaptic so im doing it manually.

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=twizitid]what the HECK does this mean and what do i do to fix it?

configure: error: conditional "HAVE_ORBIT" was never defined.
Usually this means the macro was only invoked conditionally.

this happened when trying to compile Drip, yes i tried Synaptic, something gets botched with synaptic so im doing it manually.[/QUOTE]
Well, the configure script usually checks for dependencies you need to have.  The error could be 1) you are missing a dependency, or 2) the configure script has a glitch.  You probably ought to contact the developers, mailing list, etc. and as the folks that prepared the tarball if they have any clue what it means.

---

