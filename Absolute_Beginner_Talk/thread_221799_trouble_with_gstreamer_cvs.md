---
title: "trouble with gstreamer cvs"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by bullon on 2006-07-24
hi!
i'm want to use this new music production software called [jokosher]("http://www.jokosher.org"), which requires me to use the latest gstreamer cvs...

i followed their instructions to do this (found [here]("http://www.jokosher.org/setting-up-cvs-gstreamer")) but eventually i get this error:

```
checking for XML... configure: error: Need libxml2 for glib2 builds -- you should be able to do without it -- this needs fixing
  configure failed

```

something similiar happened with bison and then flex but i just searched for the packages in synaptic, installed then and that was all. I already have a package called libxml installed, i guess its not "for glib2", anyone know what i should do from here?

---

### Post by croak77 on 2006-07-24
Try libglib2.0-0 and libglib2.0-0-dev.

---

### Post by bullon on 2006-07-24
hmmm, i already had those packages installed, I installed other glib2 packages (libglib2.0-0-dbg and libglib2.0-cil) but still have the same problem...

p.d. i'm amazed at how fast responses can be in this forum!
:KS :KS :KS :KS :KS

---

### Post by Elleo on 2006-07-25
Try also installing *libxml2-dev*. When compiling a program and it lists a library it needs it usually means that it needs the development package as well (since this is what it actually compiles against).

---

### Post by bullon on 2006-07-26
ok ,that did the trick, thanks!:)

---

