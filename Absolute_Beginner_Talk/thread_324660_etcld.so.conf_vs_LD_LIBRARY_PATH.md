---
title: "/etc/ld.so.conf vs LD_LIBRARY_PATH"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2006-12-24
I was trying to install xine-ui after installing xine-lib. libxine.so was installed in /usr/local/lib. When I did a ./configure for xine-ui, the following error was thrown:-

```
*** Could not run XINE test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding XINE or finding the wrong
*** version of XINE. If it is not finding XINE, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
***
```

So, I did:-
```
export LD_LIBRARY_PATH=/usr/local/lib
```
However, this didn't solve the problem.

So, I had to set /usr/local/lib in /etc/ld.so.conf and run ldconfig. Then it worked fine. Why wasn't the problem solved by simply setting the LD_LIBRARY_PATH variable?

---

### Post by po0f on 2006-12-24
smith.norton,

IIRC, setting LD_LIBRARY_PATH is only useful if you have different versions of a library installed on a system and would prefer to use one over the other, or the executable is compiled to look for libraries in a specific location and you want to change it.

ld.so's cache wasn't up to date when you added /usr/local/lib/libxine.so (you have to run `ldconfig` after adding libraries, it rebuilds the cache;  programs would load a lot slower if the lib paths were manually searched each time a program was opened) so it really couldn't locate the library, even though it was there.

---

