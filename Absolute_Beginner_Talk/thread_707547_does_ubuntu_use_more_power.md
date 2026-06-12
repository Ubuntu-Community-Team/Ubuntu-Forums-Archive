---
title: "does ubuntu use more power?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by tango_ninja on 2008-02-25
I have a Gateway MX6958 laptop.....just under a year old with a 6-cell battery.

A couple weeks ago, when I had my winXP system installed on the laptop a full battery charge would last me approx 3.2 hrs

Now, with Ubuntu installed I just make it to 2.0 hrs.... is it possible that Ubuntu, our resource-friendly linux OS uses sucks more power than my M$ xp ?

---

### Post by movieman on 2008-02-25
It's years since I ran Linux on a laptop, but when I was working on embedded linux recently we had problems where daemons were writing to log files on a regular basis so the hard disk would never be allowed to spin down if it wasn't in use. That significantly increased our power usage and may be the same problem you're seeing.

---

### Post by kwacka on 2008-02-25
Windows allows the processor to sleep for periods - until recently linux woke processor to check it was still working.

Situation has recently changed with Intel's 'Powertop'.

See [http://www.linux.com/articles/62091?tid=47](http://www.linux.com/articles/62091?tid=47)

Powertop is in the Gutsy backport repository.

Also, could be deteriorating battery.

---

### Post by tango_ninja on 2008-02-25
awesome this is a great utility

---

### Post by trigun on 2008-02-25
probably it's from the kernel, your hardware could be not total compatible, so acpi modules can't work very well

---

### Post by SOULRiDER on 2008-02-25
Sometimes there may be some trouble with ACPI like trigun mentiones. I cant really say much since i dont own a laptop.

---

### Post by Cha1n5aW on 2008-02-25
Personally, I find I get longer battery life out of ubuntu, backtrack, and even knoppix than I do with xp.  usually 2.5 hours battery live with linux, and anywhere from 1.5 to 2 hours battery life on xp, depending on what I'm doing.  Generally IMO linux seems to be more efficient in terms of power usage.  Hope this helps.

- Shawn

---

### Post by Whiffle on 2008-02-25
There is a whole thread about gutsy and laptop battery life, something is up with it thats making it eat battery life.  I can get pretty good life out of my battery (it estimates 3.2 hours on a full charge iirc, which is about right), but I have to be careful what I run.  I still find lots of programs randomly writing to the hard drive though, which hurts power consumption.  If i had time or another hard drive I'd install gutsy and try to help troubleshoot it, but I don't particularly care to at this point, it gave me enough problems last time I had it on here.

---

### Post by tango_ninja on 2008-02-25
hmm...so nothing hard and fast eh? I ran powertop and was able to modify a few things....i suppose i'll see how it goes in the next little while to see if its saving me power.

another thing i noticed is that often my battery life meter applet doesn't accurately reflect the life of the battery (i.e. it will say 1h 20 min left and it goes for 1h 45 min)

---

