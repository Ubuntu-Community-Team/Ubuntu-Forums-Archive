---
title: "linuxdc++: compiling issue"
date: 2005-08-25
forum: Apple PPC Users
---

### Post by Xappe on 2005-08-25
Hello,

I'm trying to compile linuxdc++ ([http://linuxdcpp.berlios.de](http://linuxdcpp.berlios.de)) on my ibook. But the developers have changed something about atomic.h that I can't figure out how to get around (it compiled fine before, but not after some cvs updates in august).

From the changelog:

"* Added a custom atomic.h (only x86 but that's easy to fix, just copy from qt =)"

Any ideas? I've been trying to figure this out for a couple of weeks now...without any luck, probably because my programming knowledge is too small...

---

### Post by DJ_Max on 2005-08-25
What error(s) do you get, it's probably some big-endian, little-endian C conflict.

---

### Post by Xappe on 2005-08-26
This is what I get:

```
client/Thread.h: In static member function ‘static long int Thread::safeInc(volatile long int&)’:
client/Thread.h:104: error: ‘ATOMIC_INIT’ was not declared in this scope
client/Thread.h:105: error: ‘atomic_inc’ was not declared in this scope
client/Thread.h: In static member function ‘static long int Thread::safeDec(volatile long int&)’:
client/Thread.h:114: error: ‘ATOMIC_INIT’ was not declared in this scope
client/Thread.h:115: error: ‘atomic_dec’ was not declared in this scope
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.
```

---

