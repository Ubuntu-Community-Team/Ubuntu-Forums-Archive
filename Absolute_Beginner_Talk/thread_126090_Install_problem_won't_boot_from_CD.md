---
title: "Install problem: won't boot from CD"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by lila on 2006-02-05
Hello,
trying to install a Dell dimension xps t600 (Pentium III, 600 mHz, 256 MBRAM, Intel SE44OBX-2 motherboard) with Breezy. 
After changing the boot sequence in the BIOS, it still won't boot from CD.  It does recognise Windows98 CD but only with start-up floppy support.   The boot sequence is set at CD-floppy-HD, but we have messed round and tried any possible combination.  It just won't.  We even tried a SuSe CD, that won't do it either.
It's funny because you can see when it starts that the CDreader comes on (read noises), then the floppy, but it just carries on without seeming to understand the CD.  I even tried a new Breezy CD just to exclude the possibility that the old one had gone mouldy or something.
I already have installed Breezy sucessfully on another machine, that was easy.  Here, I don't even get an error message...
Any ideas?:-k
Lila

---

### Post by lha on 2006-02-05
Get [rawrite]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm") and use it to write sbm.bin to floppy. Sbm.bin is on the install cd, in directory /install. You'll get a floppy which can boot from cds.

---

### Post by lila on 2006-02-05
[QUOTE=lha]Get [rawrite]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite.htm") and use it to write sbm.bin to floppy. Sbm.bin is on the install cd, in directory /install. You'll get a floppy which can boot from cds.[/QUOTE]
Thanks - took a while, but got floppy done.  Trying to boot Ubuntu as I type...
Fingers (or cables?) crossed.
Lila\\:D/

---

