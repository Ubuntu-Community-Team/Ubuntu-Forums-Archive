---
title: "&quot;make&quot; command and kernel update..."
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by searedice on 2006-10-27
I installed several updates from the Synaptic Package Manager.
It seems to have updated kernel files from 2.6.15-26 to 2.6.15-27.
There is a new folder in lib/modules/ for the new kernel code.  The old folder there, "2.6.25-26-386" has in it a "link to folder" called "build" that links to "usr/src/linux-headers-2.6.15-26-386".
This "link to folder" thing isn't in the new "2.6.15-27-386" in "lib/modules/" and there is no new-kernel equivalent to "usr/src/linux-headers-2.6.15-26-386" on my filesystem.
I have a strong feeling this is keeping me from using the "make" command to install software.
When I try to make some source files (various different programs), I get terminal output/errors like this (trying to make ndiswrapper for example):

```
make[1]: Entering directory `/home/john/Desktop/ndiswrapper-1.27/driver'
Can't find kernel build files in /lib/modules/2.6.15-27-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/john/Desktop/ndiswrapper-1.27/driver'
make: *** [all] Error 2

```

Thanks for your time,
Noob John

---

### Post by Rackerz on 2006-10-27
Did you install your Kernel headers?

---

