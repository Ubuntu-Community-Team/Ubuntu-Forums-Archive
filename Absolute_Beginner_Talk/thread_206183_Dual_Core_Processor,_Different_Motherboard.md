---
title: "Dual Core Processor, Different Motherboard?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by BitTorrentBuddha on 2006-06-29
I have a PCChips M960GV V3 motherboard. My Celeron doesn't play well with many of the hardware monitoring services including /proc. Therefore, I'm looking into upgrading my CPU sometime in the near future. I wanted to go dual core this time around, I'm wondering, will a dual core  (socket 478) CPU work on my mobo or would I have to purchase a new one for a dual core processor support (I cannot think of an way to type this into a search engine)? Also how well does Ubuntu work with dual core processors?

---

### Post by nudnik on 2006-06-29
Yes, you will need to replace the MOBO. 478 does not support the Intel dual core processors. You will need socket LGA775.

If you upgrade to LGA775, you will need a new power supply as well. Not only are the connectors different, but an Intel dual core draws much more power than the old 478 series. I suggest a name brand, high quality supply of 500W or higher, ATX 2.0.

Also, be sure to read up on the proper installation of the LGA775 heatsink, it can be difficult. Even if you get it right, dont be surprised if temps are considerably higher than your 478 CPU.

Ubuntu works fine with Intel dual core, there are custom kernels available from the respositories.

:idea:

---

### Post by BitTorrentBuddha on 2006-06-30
Thank you for the plethora of information :D . Unfortunately I don't have the initiative or funds to buy a new mobo, CPU, and PSU. So, as a follow up, would I get a significant performance increase with an upgrade to a higher end P4 with hyper threading from my 2ghz celeron? 

Also, I found [this processor](http://www.newegg.com/Product/Product.asp?Item=N82E16819111179) on newegg, it's a dual core socket 478, just to be sure, that wouldn't work with my motherboard, right?

---

