---
title: "New Hardware Q's"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-03-30
ok, I got my Abit TH7II RAID mobo today, P4 1.6GHz and
512mb RAMBUS memory. The PCB is very high quality but
it doesn't have the LAN option. Right now I'm using 56K
so will it be easy to install a LAN card in the future?

Everything works and was recognised by Ununtu 7.10
and it runs as fast as the Dual Core set up I just pieced
out.

NOTE: if you are using old hardware (the TH7II is from 2001)
be sure the BIOS is dated 2000 or higher.

---

### Post by c-ron on 2008-03-30
Ethernet cards are easy to install. Just make sure it's supported by the kernel!

---

### Post by asmoore82 on 2008-03-30
Just as a public service announcement, no agenda.

RDRAM or RIMM memory modules, marketed by the company RAMBUS,
are actually painfully slow in real world performance. The company up-sells
the technology by seriously over emphasizing the importance of clock speeds(mHz),
while simultaneously failing to mention up front, in clear terms, that traditional DIMM memory modules
use a 64-bit wide data bus while RIMMs have only a 16-bit wide data bus.
This means that RIMMs would have to be clocked a full 4X faster than DIMMs to match the same performance.

The funny thing about busting down these severely overpriced RIMM shenanigans is
that it is *all too easy* to translate fancy RAM specs(mHz) into real world **throughput**,
provided that you know the width of the data bus, of course.
So, have you ever wondered why the following are synonymous?
DDR-266 :: PC-2100
DDR-333 :: PC-2700
DDR-400 :: PC-3200

Well, let's do the math to determine the throughput of DDR-400 in MB/s.
DDR-400 is clocked at **200 mHz**, uses a double data rate(**x2**) and **64 bit** bus,  and there are **8 bits** in **1 byte**:
(200 million cycles/1 second) X 2 X (64 bits/1 cycle) / (8 bits/1 byte) = **3200 MB/s**

There you have why DDR-400 is called PC-3200, but of course this is over-simplified salesman's math
because there aren't exactly 1000 bytes in a kilo-byte, there are **1024**.
Adding that skew to the equation, we get:
(200,000,000 cycles/1 second) X 2 X (64 bits/1 cycle) / (8 bits/1 byte) / (1024 bytes/1 kilobyte) / (1024 kilobytes/ 1 megabyte) = **3051.76 MB/s**

**So, the real theoretical throughput of DDR-400(PC-3200) is 3051.76 MB/s.**

New, let's apply the same good equation to the cheapest and slowest DDR,
DDR-266 or PC-2100, which is clocked at **133 mHz**, the rest of the equation remains the same:
(133,000,000 cycles/1 second) X 2 X (64 bits/1 cycle) / (8 bits/1 byte) / (1024 bytes/1 kilobyte) / (1024 kilobytes/ 1 megabyte) = **2029.42 MB/s**

**So, the real theoretical throughput of DDR-233(PC-2100) is 2029.42 MB/s**

Now, let's apply the same good equation to RIMM(RAMBUS) memory PC-800,
which uses a **400 mHz** clock rate, also double data rate, but only **16 bit** bus:
(400,000,000 cycles/1 second) X 2 X (16 bits/1 cycle) / (8 bits/1 byte) / (1024 bytes/1 kilobyte) / (1024 kilobytes/ 1 megabyte) = **1525.88 MB/s**

**So, the real theoretical throughput of PC-800 RIMMs is only 1525.88 MB/s!**
And it comes at a price outrageously higher than any from of DDR!!

[http://en.wikipedia.org/wiki/RDRAM#Benchmarks](http://en.wikipedia.org/wiki/RDRAM#Benchmarks)

---

