---
title: "Nooobie"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by amod on 2007-02-19
guys i want to shift to Ubuntu...and am currently downloading the 6.10v...What i would like to know is wether it will work fine with the config. of my PC w.r.t the minimum requirements and any compatibility issues....
The Config. is as follows:-

Proccessor-AMD Athlon XP 2400+ @ 1991 Mhz
Motherboard- Asus A7v266-mx
ram- 256 Mb
Gfx card- Geforce 5200  fx 128mb AGP Card(8x)
Hdd- 160 Gb

Plz help me out......and i have internet via my cable operator who doesn't seem to have a dialer for linux....it goes by da name of '24 online on able' something......would like to know wether i will be able to access the net??????

---

### Post by sloggerkhan on 2007-02-19
don't know about your internet. But you should be able to test it all off of the live CD without installing, even if it will be really slow off a CD with 256 megs of ram.  You MIGHT consider xubuntu. I'd say you have the processor and graphics power you need, but the RAM seems a little bit lacking to me. Not too sure.

---

### Post by amod on 2007-02-19
Do we get soundmax drivers for linux?????

---

### Post by deadgobby on 2007-02-19
Often when installing Ubuntu i386 on an AMD64 board you will have to hit F6 and enter the following paramaters

irqpoll pci=noacpi noapic nolapic acpi=off

to get The Ubuntu i386 Alternate or LiveCD to Boot correctly. 
 Your sound card may be autodected. If it runs OK on the live CD, you'll know it will owrk just fine.

---

