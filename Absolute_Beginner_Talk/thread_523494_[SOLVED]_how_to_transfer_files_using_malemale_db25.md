---
title: "[SOLVED] how to transfer files using male/male db25 cable"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-08-12
Hi Guys,

I have a stupid question. I just bought a new HD for my laptop (bare drive) and the enclosure I ordered is not coming until mid next week so I thought I can transfer the 10 gigs of documents I really need to an old laptop and then copy them back once I remove the current and install the new HD.

I happen to have a male/male (parallel) DB25 cable, but I know nothing about this. Where should I start? (both laptops have parallel ports)

Thanks,
D.

---

### Post by davidsrsb on 2007-08-12
you are looking for the linux eqivalent of "direct cable connection". This is "pppd"
see [http://howto.gumph.org/content/xp-direct-cable-to-linux/](http://howto.gumph.org/content/xp-direct-cable-to-linux/)

Still very slow and fiddly to get working.
It would be much easier and quicker to use an Ethernet crossover cable

---

### Post by steve.horsley on 2007-08-12
A quick calculation says that at 120kbit/s, which I think is around top speed for a serial port, the data transfer of 10 Gig will take just under 10 days. I recommend you don't bother. As davidsrsb says, Ethernet with a crossover cable would be a reasonable approach.

---

### Post by davidsrsb on 2007-08-12
Jdrodrig was talking about the parallel port, which is capable of 1MB/s on a good day. Ethernet would manage about 10MB/s and a lot less hassle, as Linux parallel port support is far from complete

---

### Post by steve.horsley on 2007-08-13
> **davidsrsb said:**
> Jdrodrig was talking about the parallel port, which is capable of 1MB/s on a good day. Ethernet would manage about 10MB/s and a lot less hassle, as Linux parallel port support is far from complete

Oops. My bad. 
But I don't know if p-p is possible over parallel cable, or what software to use even if the hardware is capable. I stil vote Ethernet. Or a few chunks via memory stick.

---

### Post by jdrodrig on 2007-08-14
Thank you all guys!

After evaluating the situation, I will wait for my enclosure to arrive (hopefully tomorrow)

---

