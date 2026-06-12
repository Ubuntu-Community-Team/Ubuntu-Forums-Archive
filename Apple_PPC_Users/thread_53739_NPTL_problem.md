---
title: "NPTL problem"
date: 2005-08-01
forum: Apple PPC Users
---

### Post by craks on 2005-08-01
As wo all know, nptl is more faster than linuxthreads. But i check my enviroment

getconf GNU_LIBPTHREAD_VERSION, the result is
linuxthreads-0.10, but not nptl 0.6*

any one have known why ubuntu choose linuxthreads, nptl is the excited feature under kernel 2.6 in glibc.


 :-|  :-|  :-|  :-|  :-|  :-|

---

### Post by plasmatonic on 2005-08-16
Ah yes... NPTL...

The speedups are highly noticable,  but it is known to cause problems with glibc and many shared libs.  Unfortunatly, the compatability of NPTL, even with pthreads installed seperately, is not 100%. For me, Alias's Maya (any and all versions) will not work with nptl, and that is not something I can work without ;) There are workarounds to many of the known errors with NPTL, but Maya is not one of them, not to mention the ammount of time you could invest in getting an older binary package to work with nptl wouldn't offset the speed increase in the next hundred years  ](*,)

EDIT: Hoary, should by default be using NPTL btw, I however recommend against it. Nonetheless, check to ensure libc6-i686 is installed, as that will provide your nptl support.

---

### Post by ctaggart on 2005-10-10
I'm runnin the live cd from ubuntu-5.10-rc-live-i386.iso.  I verified that libc6-i686 is installed and the output from getconf is:

ubuntu@ubuntu:~$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.3.5

Now I just need to verify that the kernel is configured to support NPTL...

---

