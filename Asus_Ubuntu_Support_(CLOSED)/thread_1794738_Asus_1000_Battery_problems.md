---
title: "Asus 1000 Battery problems"
date: 2011-07-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cozzyb on 2011-07-01
Hi there,

new to Ubuntu and bought a asus 1000 linux version recently off someone, first thing I did was change to Ubuntu, all works well except battery readings.

The 6600mh battery reads as 41% capacity, which is bad, but I know this is wrong because when it hits 0 it keeps on going for another hour or so.

I just bought a brand new 12000mh battery online, sealed etc, and it was at 40% charge, but the capacity reads as 12% :? , I don't understand what is going on with the API on this laptop and Ubuntu, haven't tried any other OS s to see if this is different on these.

Any ideas?

On latest bios and latest ubuntu

---

### Post by Jouke74 on 2011-07-14
If you have boot booster on, turn it off. Boot booster saves the BIOS settings to disk to rapidly read them out, but if you have changed your battery then the info of the old battery is still in this data, not the info of the new one (it does not update). This messes up the readings. 

Furthermore, the new battery info also needs to be stored into the BIOS itself to work. When putting in the new battery, go to your BIOS, change something to off and put it back on, then save changes. Then let your laptop boot. 

Afterwards the acpi meter should work. 

I had the same problem, but the other way around, my battery did not want to fully charge (stopped at 88% which is 4400 out of the 5200 mh).

If all reads out correctly you can put on boot booster again, and new data will be written to disk.

Note that, if you put in a different battery the procedure has to be repeated.

---

