---
title: "macbook 4.1 taking more than 4 mins to boot(intrepid"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by yasasvy on 2008-11-04
Hi i just recently updated to 8.10 from 8.04 on my macbook 4.1.. 

8.04 used to boot normally but 8.10 takes ages to do it.. i jus did a normal upgrade and i kept the old config files while updating though. 

I am attaching the boot sequence of my laptop.

---

### Post by misterlister on 2008-11-06
Consider yourself lucky, I upgraded the same way and now have to endure 5 + minute boot times, ~4 of which are spent doing nothing... alas, back to Leopard it is.

PowerPC G4  (2.1) 1GHz x2 
1.25 GB RAM

---

### Post by _mario_ on 2008-11-06
> **yasasvy said:**
> 
8.04 used to boot normally but 8.10 takes ages to do it.. i just did a normal upgrade and i kept the old config files while updating though.

i did the same (while intrepid was still beta) on a MacBookPro 4,1 and it worked. after having a look at your log, it looks like the machine waits for some network timeout. so just a question: does it work if you connect the machine to a network (with DHCP) before booting? do you have something unusual configured?

ciao,
Mario

---

### Post by yasasvy on 2008-11-07
Yeah I have tried that and the times havent improved. Well I have blacklisted a few modules while on hardy (ssb,oss) also the laptop idles while loading alsa-base. Any possible solutions?

---

