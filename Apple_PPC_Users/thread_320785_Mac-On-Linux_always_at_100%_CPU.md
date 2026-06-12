---
title: "Mac-On-Linux always at 100% CPU"
date: 2006-12-17
forum: Apple PPC Users
---

### Post by paulsomm on 2006-12-17
I'm running 6.10 and have installed Mac-On-Linux, which I've used since 6.06 beta days with no issues.  Under 6.10, however, MOL is always at 100% CPU and if I look at the Process Viewer in OSX, it's from "KERNEL_TASK".

MOL also takes upwards of 2 minutes to go from the penguin screen to actually booting OSX as well, with the CPU at 100% the entire time.

It's not my installation of OS X.  I've done a fresh-from-scratch install of 10.3, and then 10.4, to no avail.  Same issue on both, as base builds and as fully patched OS X installs.

Does anyone know why or what a solution is?

Thanks in advance

---

### Post by niccoswe on 2008-01-19
I'm having the exact same problem. Should it be this way? If so, it really lowers the usability of MOL, especially when running on batteries.:confused:

---

### Post by stmiller on 2008-01-19
Support for 10.4 in MOL only came in with the more recent releases. Are you using the provided ubuntu packages? If so they are out of date, and have many bugs. It's best to fetch the latest SVN if possible.

---

### Post by niccoswe on 2008-01-20
Thanks, got it to work after i compiled the latest release. With netwok and everything. Really nice, hope it's stable enough to use in the long run.

---

