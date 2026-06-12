---
title: "Eee Pc 1015PEM with 4 cores???"
date: 2011-06-30
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Chris11 on 2011-06-30
Hy there, I bought a Ecc Pc 1015PEM and installed Ubuntu 11.04, everthing is working reat and smooth, but the sys monitor shows 4 cores working...

[IMG]http://dc379.4shared.com/img/gMV2wnLl/s7/0.6306383527211622/SysMon1.png[/IMG]

is there anything to worry about that?

Thanks, Chris

---

### Post by BCingyou on 2011-06-30
that is very odd indeed... 

try installing "hardinfo" from software centre, and then run it and see what it says under processors.  Hardinfo will appear as "system profiler and benchmark" in the unity menus.

---

### Post by Chris11 on 2011-06-30
Device > Processor shows:

> Intel(R) Atom(TM) CPU 550 @ 1.50 Ghz 1500.00Mhz
Intel(R) Atom(TM) CPU 550 @ 1.50 Ghz 1500.00Mhz
Intel(R) Atom(TM) CPU 550 @ 1.50 Ghz 1500.00Mhz
Intel(R) Atom(TM) CPU 550 @ 1.50 Ghz 1500.00Mhz

---

### Post by nicocarbone on 2011-06-30
That's because the Intel Atom 550 is a two core CPU with hyperthreading [http://en.wikipedia.org/wiki/Hyper-threading]("http://en.wikipedia.org/wiki/Hyper-threading") . That means that there are two logical "cores" for every physical one.
It's perfectly normal.

---

### Post by Chris11 on 2011-06-30
thank you!

---

