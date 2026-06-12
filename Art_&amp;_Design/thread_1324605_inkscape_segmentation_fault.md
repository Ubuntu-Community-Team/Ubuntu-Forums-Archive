---
title: "inkscape segmentation fault"
date: 2009-11-12
forum: Art &amp; Design
---

### Post by zieglerj on 2009-11-12
Despite repeated attempts I can't get inkscape to work on my Ubuntu 9.04 machine. I've checked all the dependencies listed on the inkscape site and have them all installed but nothing . . . 

When I try to run it from terminal it spits out segmentation fault. 

Any thoughts?

---

### Post by zieglerj on 2009-11-14
Help, anyone?  I keep hearing what a great program this is but it flat out won't work on my system. What would cause this?

---

### Post by bubblehead74 on 2009-11-15
I can't help you unfortunately. I can only attest that Inkscape 0.46 works flawlessly on my 9.04. I installed it using the Synaptic and never encountered any problem. I use it for scientific publishing and I find it very productive.

---

### Post by hessiess on 2009-11-15
> **zieglerj said:**
> Despite repeated attempts I can't get inkscape to work on my Ubuntu 9.04 machine. I've checked all the dependencies listed on the inkscape site and have them all installed but nothing . . . 

When I try to run it from terminal it spits out segmentation fault. 

Any thoughts?

Did you install it form the ubuntu repository or from a download form the inkscape website.

Saying that it segfaults is not very helpful, there are loads of things which can cause something to segfault. Running it through GDB and reporting a bug to the inkscape project would be your best bet.

---

### Post by zieglerj on 2009-11-15
I've tried it installed both ways. How do I run it through GDB?

---

### Post by hessiess on 2009-11-16
> 
I've tried it installed both ways

You rilley want to avoid doing this, atleast make sure to remove one version before installing another. Its possible the two installed could be `tripping over each outher' and using different versions of libs.

Run ``sudo apt-get --purge remove inkscape'' to remove the repo version, then CD into the source directory you used to install it manually and run `sudo make uninstall'. Then install it again from the repo.

Type `gdb inkscape', wait for the prompt(gdb) to come up then type `run'. Hopefully the version in the repository still has debugging symbols in it. That will tell you where the program is segfaulting, then report a bug with the full GDB output to the inkscape team.

---

### Post by zieglerj on 2009-11-17
This was the result: 

> GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/bin/inkscape 
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f3bdf904790 (LWP 19809)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f3bdf904790 (LWP 19809)]
0x00007f3bd959bda5 in GC_malloc (bytes=256) at thread_local_alloc.c:176
176	    GC_FAST_MALLOC_GRANS(result, granules, tiny_fl, DIRECT_GRANULES,


---

