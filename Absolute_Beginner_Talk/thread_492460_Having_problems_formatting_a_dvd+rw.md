---
title: "Having problems formatting a dvd+rw"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by AmandaKerik on 2007-07-04
The label says it's a DVD+R and there's a RW on it, so that means it's a DVD+RW, right?

It was previously burned by Windows XP Media Center - the one file on the disk is proprietary MS, etc. 
Could the problems be caused by the fact that the file on there was written by MS?

I just want to format / wipe the disk for new uses and I can't seem to manage it.
I've Googled the problem, but most of them say the same thing - to use:
# dvd+rw-format -blank /dev/cdrw

I even found the technical place for the dvd:
# dvd+rw-format -blank /dev/hdc

(Without the # I presume)

I always get the same response: * BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
:-( mounted media doesn't appear to be DVD±RW, DVD-RAM or Blu-ray

Yet when I try to burn to it using the cd / dvd creator, it's only problem is there's not enough room.

How do I change the permissions so it'll wipe the DVD?

[Edit]
I've even tried:
dvd+rw-format -blank cdrom0

The response: * BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
- usage: dvd+rw-format [-force[=full]] [-lead-out|-blank[=full]]
         [-ssa[=none|default|max|XXXm]] /dev/dvd

I'm getting a bit flustered here...

---

### Post by mysticrider92 on 2007-07-04
You might just want to try Gnome Baker (sudo apt-get install gnomebaker). That is probably the best Linux burining program and it can blank cd-rw's and dvd-rw's. The command-line programs can be somewhat hard to use. Also, if you do use the format program, maybe try it with sudo since you might not have access to the /dev folder for an unmounted drive.

---

### Post by blastus on 2007-07-04
[quote=AmandaKerik]The label says it's a DVD+R and there's a RW on it, so that means it's a DVD+RW, right?[/quote]

Not necessarily. For example, Fujitsu DVD+R discs have RW written on them but they are DVD+R. If the disc truly is a DVD+RW then I'm not sure what the solution is. I've never ever been able to burn a DVD+RW in Linux. But DVD-RW burn no problem.

---

