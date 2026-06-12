---
title: "What's /dev/null for?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by happysmileman on 2007-11-17
I was wondering, and what's /dev/null actually for? It appears to be a pseudo-device that just gets things piped to it and does absolutely nothing with them, am I missing something or is this correct.
And if so, why bother piping things to it in the first place, just to have nothing done

---

### Post by Onyros on 2007-11-17
/dev/null is a black hole. :)

It sucks.

Or you can be nihilist about it, and embrace its nothingness. (Or wholiness, depends on your point of view).

---

### Post by toxin on 2007-11-17
From wikipedia:

> In Unix-like operating systems, /dev/null or the null device is a special file that discards all data written to it (but reports that the write operation succeeded), and provides no data to any process that reads from it (it returns EOF). In Unix programmer jargon, it may also be called the bit bucket or black hole.

The null device is typically used for disposing of unwanted output streams of a process, or as a convenient empty file for input streams. This is usually done by redirection.

This is sometimes useful with command line programs, mostly in scripts.

---

### Post by brennydoogles on 2007-11-17
> **toxin said:**
> From wikipedia:



This is sometimes useful with command line programs, mostly in scripts.

What would be one example that it could be useful?

---

### Post by spec-chum on 2007-11-17
If you're doing a find and you're not interested in any errors that it throws up about not being able to access folders etc then it comes in very handy as you can redirect standard error to the null device to not show them, for example

```
find / -name fred -print 2>/dev/null
```

That will find all files called fred in your system and ignore any access errors the find command gets by throwing them away to /dev/null.  Very handy thing /dev/null is.

---

