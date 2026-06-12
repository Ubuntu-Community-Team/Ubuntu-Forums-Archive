---
title: "Frighteningly deep directory..."
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-12
Hi all,

For giggles, I ran F-Prot (anti-virus) system wide.  I didn't find anything except the dummy virus, of course, but I did see this terror:

Error on scanning /dev/fd/7/dev/fd/7/dev/fd/7/dev/fd/7/dev/fd/7/var/lib/tripwire/report/X(access denied)

There are about 20 instances of that (/tripwire/report/X being an example of an app that appears after that final /lib).  

While redundancy is something I like where machines are concerned, especially on airplanes and such, this is going maybe a little too far.  Does this beast appear on your machine?

Rock over London, rock on Chicago,

therunnyman

---

### Post by joft on 2006-04-13
Hi,

Usually /dev/fd is a symbolic link to /proc/self/fd - and that's the point. /proc isn't a "real" filesystem. There are no "real" files, they just look like they are "real" files. The /proc filesystem is a kind of "window" into the Linux kernel's internal "variables"/"configuration items".

IMO you should exclude /proc (and /sys, too) from your F-Prot scanning process.

---

### Post by therunnyman on 2006-04-14
That so postmodern...they're there...but not!

Thanks kindly for the help.  After leaning about /proc weirdness, I decided it might be best to exclude /proc from my Tripwire policy file.  125,000 line reports were bringing me down, just a little.

therunnyman

---

