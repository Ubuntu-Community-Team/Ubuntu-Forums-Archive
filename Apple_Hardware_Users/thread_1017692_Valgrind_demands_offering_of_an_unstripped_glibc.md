---
title: "Valgrind demands offering of an unstripped glibc"
date: 2008-12-21
forum: Apple Hardware Users
---

### Post by JFASI on 2008-12-21
Machine: Quicksilver G4, 966Mhz. 

Ok, so when I try to run valgrind, it outputs the following message: 

```
==17187== Memcheck, a memory error detector.
==17187== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==17187== Using LibVEX rev 1804, a library for dynamic binary translation.
==17187== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==17187== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==17187== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==17187== For more details, rerun with: -v
==17187== 

valgrind:  Fatal error at startup: a function redirection
valgrind:  which is mandatory for this platform-tool combination
valgrind:  cannot be set up.  Details of the redirection are:
valgrind:  
valgrind:  A must-be-redirected function
valgrind:  whose name matches the pattern:      strlen
valgrind:  in an object with soname matching:   ld.so.1
valgrind:  was not found whilst processing
valgrind:  symbols from the object with soname: ld.so.1
valgrind:  
valgrind:  Possible fix: install glibc's debuginfo package on this machine.
valgrind:  
valgrind:  Cannot continue -- exiting now.  Sorry.

```


Now I pretty much know why this is happening. Valgrind wants to redirect strlen (and doubtlessly dozens of other functions that it failed before it could reach), because its ppc32 and pcc64 versions of those functions tend to yield horrifying false positives, rendering it useless on those platforms. 

When it installed, it installed glibc-dbg, which is unstripped, as a dependency. I added /usr/lib/debug to $LD_LIBRARY_PATH, and after compiling my code, I found that the output given by various failures I planted within was consistent with what I'd expect from an unstripped glibc. 

So here is the heart of my problem. On Gentoo, which is usually my flavor of choice, and which I have abandoned because my dependency trees got *really* ugly, I simply set a FEATURES flag SPLITDEBUG, and when I recompiled glibc, the debug version was the only one present on the machine. Ugly, I'll admit, but very powerful. 

Obviously, this is not an option on Ubuntu, since it's not nearly as low down as Gentoo. So since replacing the freaking glibc is not an option, how can I make Valgrind work?

---

### Post by thompson42 on 2010-01-26
Installing the libc6-dbg package fixed this problem on my Intel Xeon x86_64 system.

The package description says, "GNU C Library: detached debugging symbols".

Please excuse me for replying to an old thread, but this thread is at the top of the Google search results for this error, so perhaps this reply will help others, if not the OP.

---

### Post by sitaktif on 2013-02-01
Don't apologise for answering a question!

And thank you for answering :)

---

### Post by olifre on 2013-05-01
My thanks, too!

As this thread is really high up in the search results, I wanted to add that the OP is mistaken about some things: 
- Adding /usr/lib/debug to $LD_LIBRARY_PATH does not make any sense, as this directory contains only the debug-symbol-portions of the libraries. This directory is automatically searched by programs like valgrind / gdb for debug symbols matching the installed libraries if these are stripped. 
- "SPLITDEBUG" on Gentoo actually does something similiar to what is done for Ubuntu / Debian, namely splitting off the debug symbols from glibc and finally stripping it. 
**This means the installed libraries are stripped, but the debug symbols are extracted to /usr/lib/debug before, and only loaded if actually needed!** If you use gentoo, you might also want the feature "installsources" to do sensible debugging and "compressdebug" to save some space.

---

