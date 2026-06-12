---
title: "Man Page Association"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by gamechampionx on 2007-04-17
I've got a question about how man pages are associated to commands.

I've recently installed JDK 6, and in messing around, I've got the java man page to somehow not exist.  "man java" fails to work, although "man javac" works, and both commands work from the command-line.

I'm not really sure of how man associates a page to a command but I somehow need to figure out how to reassociate the correct man page to the java command because I think I broke that association somehow.

Is there are way to modify that information easily?

---

### Post by jerryrw on 2007-04-17
Not all packages have man pages.  Some use info, others just have html/xml help docs.  man pages aren't really associated per se.  The installation script really should take care of putting them in the right place. Check the sub dirs of /usr/share/man for the actual man pages.  Depending on how the pages are shipped in a particular app the process of installing them can be easy or very complex.

---

### Post by jerryrw on 2007-04-17
You can also try a:

```
man -u
```

To rebuild the database of available man pages.

---

### Post by gamechampionx on 2007-04-17
Thanks for the reply.

The thing about the java command is that man originally redirected it to gij.
From what I can remember, the Java6 installation is supposed to re-associate it to the newly-installed java command.

I tried using the -u parameter but it didn't really seem to change the situation at all.

I think this is a case of me breaking something as usual.  I think the lesson of the day might be to not muck around with stuff.

---

