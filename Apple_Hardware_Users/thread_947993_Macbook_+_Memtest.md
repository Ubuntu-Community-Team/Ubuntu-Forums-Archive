---
title: "Macbook + Memtest"
date: 2008-10-14
forum: Apple Hardware Users
---

### Post by conundrumx on 2008-10-14
Hi all,

I have a first generation Macbook (2ghz Core Duo, GMA950) for which I just bought 2 gigs of RAM.  I installed the memory just fine, booted into OSX and everything seemed good.  However, due to my own cautious nature I grabbed an Ubuntu disk from my work supplies (my Thinkpad runs Hardy) to test the new memory.  I got 199 errors from a brand I have had nothing but good experience with, and both the numlock and capslock lights were on (Kernel panic?)

Add this to the wrong memory speed being reported by Memtest, it's all a bit fishy, and enough to give pause before RMAing this stuff.

Long story short:  Anyone else had Memtest86+ give false positives on a Macbook?

---

### Post by Developer.ca on 2008-10-17
Matt Johnston has patched memtest to work on Intel Macs.

[http://matt.ucc.asn.au/memtest/](http://matt.ucc.asn.au/memtest/)

It needs a grub patch (possibly already applied, since you are already able to run it), and he's patched it to ignore the bottom 1.2M of memory, as it seems to be used for the system, but the Bootcamp bios doesn't seem to mark it as unusable.  The symptoms that occur without the patch are spurious errors, plus the numlock led will blink (sounds exactly like what you are seeing).

He also says that the memory timings are wrong and vary on each run.  The same thing you are seeing.  (This is interesting...I found this page and his because I was specifically trying to find out what the memory timings are on stock Apple RAM...it seems to be a hard thing to find, and somehow even memtest can't figure it out).

I'd say stock Memtest on a Macbook gives false positives in the lowest 1.2M, and your ram is fine.  If you want to be absolutely sure, I believe you can set the range of memory to test in memtest, so you can raise the bottom just above 1.2M and retest.

---

### Post by sunbird on 2009-04-07
Hey, so I just upgraded the memory on my machine (MBP 3.1) and got the dreaded "Starting up..." screen when I try to load memtest. Everything else seems to work fine.

I'm wondering whether anyone has tried this patch on a MBP 3.1 or if there are any other options for running memtest. I'm surprised there isn't anything in the mactel repo for this purpose.

Any ideas?

---

