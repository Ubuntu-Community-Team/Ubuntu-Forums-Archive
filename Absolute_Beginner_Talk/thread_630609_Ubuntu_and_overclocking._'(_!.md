---
title: "Ubuntu and overclocking. :'( ?!"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-12-03
I use my bios to overclock my C2D E6600 to 3.3ghz (It's 2.4ghz stock). It always worked with windows and was a very stable clock. So I went and installed Ubuntu gusty for dual boot. Everything works great and I'm living gusty. But my cpu clock went down to stock clock setting. It says it's still enabled in my bios, but it's not overclocking???. I tried underclocking and overclocking and many options, nothing changed my cpu clock. The only thing that responded is changing my CPU multiplier. But that doesn't help my get to my old 3.3ghz clock. I'm typing this fast because I got to go to work, so I'll give more info later. But I guess my question is, why isn't my bios working?????? Why would installing Ubuntu make my bios unable to overclock???? Any help would be greatly appreciated.

---

### Post by speed145a on 2007-12-03
how are you checking the clock speed?

depending on how you are doing this ubuntu may just be telling you what the processor is identifying itself as, not the actual clock speed

---

### Post by fatality_uk on 2007-12-03
I presume you've changed the voltage. So reset your BIOS to default, then run something from this list

[http://lbs.sourceforge.net/](http://lbs.sourceforge.net/)

Haven't checked but I guess theres a CPU benchmark in there. Get a baseline figure for your default system and then o/c and run again. Even if Linux doesn't represent the o/c'd CPU speed it might show in the benchmark

Got me thinking!!!
Does anyone know anything about Powertweak-Linux??????

---

### Post by Comzee on 2007-12-03
> **speed145a said:**
> how are you checking the clock speed?

depending on how you are doing this ubuntu may just be telling you what the processor is identifying itself as, not the actual clock speed

Yea, I've already done that. I ran a windows multi-core cpu benchmark when my cpu was o/c. It was 10500. Now it's only getting 7400. My start up screen says it's 2.4ghz. Both windows and Ubuntu tell me it's 2.4ghz. The only thing thats crazy is the bios tells me that the CPU is being overclocked. So now theres no way I can overclock because my bios says it's already being overclocked. There was no problem before I installed Ubuntu for dual boot. I don't know why that would prevent the motherboards bios from overclocking the CPU??????

If I don't get this fixed I might have to uninstall Ubuntu and single boot windows. The performance gain is too much to loose. :(

---

### Post by Flying caveman on 2007-12-03
I over-clocked my desktop computer through BIOS, the cpu freq monitor didn't reflect the change but I did ran super_pi and it was definitely faster.

---

### Post by Comzee on 2007-12-03
Fixt. My cmos got corrupted because I had an unstable CPU frequency during the Ubuntu installation. I had to reset the cmos on my motherboard.

---

### Post by BENdage on 2007-12-04
ah-ha, I'll bet thats what happened to mine, thanks for the info

---

### Post by Joeb454 on 2007-12-04
if you've sorted it please mark the thread solved :) means other people can look through and find there is an answer in this thread somewhere :)

---

