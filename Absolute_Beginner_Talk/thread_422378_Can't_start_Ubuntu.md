---
title: "Can't start Ubuntu"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Rob2Kx on 2007-04-25
Hi, quick question:

In group and User settings I changed my home directory from home\rob to \

Now I can't start Ubuntu.  I get an error message (I can't remember the exact message, because I'm at my friend's place using his computer).  But the jist of it is that I shouldn't have done what I did.

I can start Ubuntu using the console, but I don't know any commands that would change my home directory back to what it was.  Any info would be appreciated.

Thanks!

---

### Post by jhnthn on 2007-04-25
Check /etc/passwd in vim. Look for your username. The line should say something like this (maybe):
```
Rob:x:1000:1000:,,,:/:/bin/bash
```
If it does try changing it to:
```
Rob:x:1000:1000:,,,:/Rob:/bin/bash
```

---

