---
title: "which kernel for dual core pentium 4 kubuntu 6.10?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by monkman on 2006-11-14
hi, i'm missing the right kernel for the above named cpu.

just a generic one, never heard of this before...
6.06 there where a lot of more options.
what to choose now?

thx...

---

### Post by igknighted on 2006-11-14
Generic supports all of the various kernels that were in dapper, there is no need to swap it out... it should even have SMP support.

are you sure thats a dual core and not just hyperthreading?  I wasn't aware they made a dual core P4

---

### Post by monkman on 2006-11-14
it's a pentium d 805

---

### Post by igknighted on 2006-11-14
Ah... that kernel shouldn't cause any issue for you, I wouldn't worry about it.  Ubuntu uses generic because they want to fit as many apps as they can on the live CD and lots of kernels take up space (or at least this is what I have been told).

---

### Post by JayTee on 2006-11-14
The most recent kernel in Dapper is 2.6.15-27 and requires the i686 kernel for dual core SMP but the kernel in Edgy is 2.6.17 or 18 and is a generic kernel with support for all the various Intel CPUs and AMD. Not sure about PowerPC but with a Pentium D your generic kernel should work just fine. Open the System Monitor and you should see two CPUs on the Resources tab. I'm running a Pentium D 940 and in Dapper with the right kernel it recognizes both so the generic in Edgy should too right out of the box (or CD in this case)

---

