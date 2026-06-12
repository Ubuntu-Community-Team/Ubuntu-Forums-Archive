---
title: "&quot;Deadmoo&quot; OSX86 Help"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by panipuri on 2008-03-10
Okay, so I have installed ubuntu on a 40 gig partition and used another 20 gigs to "dd" the tiger-x86-flat.img. I look at the partition from ubuntu and it seems to have written it properly and looks like it can be booted from (OSX). But I added several different entries to GRUB to boot from this partition and I get multiple errors.

1)  title MacOSX
 root (hd0,1)
 chainloader --force +1

I put this in menu.lst file and when I boot it, I get "Starting Up..." and it doesn't do anything after that.

2) title OSX_X86
 rootnoverify (hd0,2)
 makeactive
 chainloader +1

And I get "Error 12, invalid device requested"

My partition is set to (hd0,1)

What to do?

And by the way, the pc i am using is a Intel Pentium M SSE2

---

