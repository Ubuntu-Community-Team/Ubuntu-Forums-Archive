---
title: "Unix &amp; Linux"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by glaurens on 2008-01-26
This may be an extremely dumb question, but will programs written for Unix run in Linux?

---

### Post by jan quark on 2008-01-26
[http://en.wikipedia.org/wiki/Unix](http://en.wikipedia.org/wiki/Unix)
[http://en.wikipedia.org/wiki/Unix-like](http://en.wikipedia.org/wiki/Unix-like)
[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)
they should

if you have free time something to read:)

---

### Post by PeterJS on 2008-01-26
Depends what format they're in. If you've got binaries, I wish you the best of luck and suggest that you don't hold your breath. If you've got source, it should compile, should. The trick there would be getting the right library headers and versions. There's nothing about unix that implies ancient, but that comes to mind, you might run in to problems if libraries have changed to radically since it was originally written.

In theory, POSIX code should build on any POSIX compliant (or 99% compliant in the case of linux) operating system, the fact comes down to can you get the right versions of the headers.

---

