---
title: "Help installing"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by igoclimbingnaked on 2007-07-31
Ive installed it before but when i do it crashes on the boot.
So now im just trying to get it to work from the live cd. And im thinking all i need is a (boot: ) command. Seeing as there are a few suggestions for that on the live cd.

When i try to boot from the live cd it starts to but when it gets to Loading Hardware Drivers It spits out a bunch of text (that i dont know what it means) and then freezes
The last line of text it shows is

EIP: nativ_apic_write_atomic+0x6/0x10 SS:ESP 0068:e49fbe8c

Its a dell dimension 2350 with some not stock items
The mother board is a Mitac with a Intel 845 (brookdale) Chipset
My processor is an intel pentium 4 with 2.0 ghz
My graphics card is an Nvidea GeForce4 MX 4000
I have roughly 750mb of ram
My hardrive is a WDC WD400BB-75FJA1 40gb ata

---

### Post by kmslinux on 2007-07-31
I Googled it and it came up with an ubuntuforums post. Yours! I can't really find anything about it, but did you try the alternate CD?

---

### Post by igoclimbingnaked on 2007-07-31
yah ive installed it before with the alternate but it would never succesfully load...it would just freeze 3 bars into the loading bar

---

### Post by Svictor on 2007-07-31
Hi,
You could try adding something like
```
noapic,nolapic,acpi=off
```
to the boot options. This would mean disabling apic and acpi. It's just a guess (the last line you see is about apic). 
Also, make sure you remove any "quiet" and "splash" options in the boot line, so you get all the information availible. Maybe there is some clue in there. Good luck !

---

### Post by igoclimbingnaked on 2007-07-31
yah that didnt change much of anything it still crashed at the same point

---

### Post by igoclimbingnaked on 2007-08-01
bump

---

