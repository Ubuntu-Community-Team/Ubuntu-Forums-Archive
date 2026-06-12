---
title: "DVD Burner problems - massive failure rate"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by barkerben on 2006-11-05
Hi,

I've just put together a HTPC system running ubuntu or a dual core 64 bit AMD system. My kernel version is 2.6.17-10-generic

Most things seem to be working ok - but the DVD drive is acting up. The drive is a NEC 7173 18x18, but is identified by linux as an optiarc dvd rw ad-7173a.

I have succeeded in writing CD's - but the failure rate is high. DVD's never report any errors, but generally only some of the data is readable. For example when I was writing 5 .avi's to a DVD only two played, the rest were identified as text files...

Does anyone have any suggestions? Is it a problem with the mismatch in what linux thinks the device is and what it actually is?

Cheers,

Ben

---

### Post by PriceChild on 2006-11-05
Try burning at a slower speed.

---

### Post by gn2 on 2006-11-05
Or try different blanks? Not all dyes suit all drives.

---

### Post by barkerben on 2006-11-06
I tried burning at a far lower speed - the results were better, but still bad. With CD's the results were no better at all. I'll try getting some new blanks this evening and see if that helps...

Ben

---

### Post by barkerben on 2006-11-06
Ok - it was a simple solution after all. A combination of slower writing speed and less cruddy dvd's and everything worked fine :-)

---

### Post by gus sett on 2007-03-11
**UPDATE** solution describe in original thread
haven't worked on unix since Linspire in Dec, but you have company
of assorted types--try HP laptop optiarc as a search string.  On Vista
my 8X ad-7530a DVD drive couldn't tell that .mpeg files were video
format, though it wrote them to the disc.  An entirely different drive
under XP could read the same disc.

> **barkerben said:**
> Hi,

I've just put together a HTPC system running ubuntu or a dual core 64 bit AMD system. My kernel version is 2.6.17-10-generic

Most things seem to be working ok - but the DVD drive is acting up. The drive is a NEC 7173 18x18, but is identified by linux as an optiarc dvd rw ad-7173a.

I have succeeded in writing CD's - but the failure rate is high. DVD's never report any errors, but generally only some of the data is readable. For example when I was writing 5 .avi's to a DVD only two played, the rest were identified as text files...

Does anyone have any suggestions? Is it a problem with the mismatch in what linux thinks the device is and what it actually is?

Cheers,

Ben

---

### Post by drewbert on 2007-03-14
I have been having a similar problem except that all the software spits out my blank DVDs and sais I should be using a CD....even the built in burn DVD feature in ubuntu doesn't work....I'm just trying to backup some data and can't seem to do it.  I have a SONY dvd burner....gets detected properly, i try to use nero linux, gnomebaker and the built in burning app....nothing works....just an error message......different for each app but basicaly says i can't burn to DVDs

---

### Post by drewbert on 2007-03-14
I fixed my problem...it was a bone-headed oversight on my part.....good luck all with your problems.

---

### Post by gus sett on 2007-03-14
...so which SONY drive was this?--if you clarify the oversight, you remind readers
at best, entertain at worst #-o 

> **drewbert said:**
> I fixed my problem...it was a bone-headed oversight on my part.....good luck all with your problems.

---

