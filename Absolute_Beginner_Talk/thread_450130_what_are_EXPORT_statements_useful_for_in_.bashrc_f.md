---
title: "what are EXPORT statements useful for in .bashrc file"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-05-21
what are EXPORT statements useful for in .bashrc file ?

I see something like this:
export JAVA_HOME=/usr/lib/jvm/jre1.6.0/

What good does that line do for me? Any examples?

---

### Post by raeb on 2007-05-21
export sets environment variables.  in that java example, the java software may be installed anywhere on your machine.  however, all a program has to do to find java is look at the environment variable JAVA_HOME.  Here's the man page if you're more curious.

[http://www.ss64.com/bash/export.html](http://www.ss64.com/bash/export.html)

---

