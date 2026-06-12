---
title: "Program to Monitor Voltages and Temperatures?"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-07-23
Or at least the voltages during normal operation, if not both.

Thanks for any help.

---

### Post by jasmuz on 2005-07-23
Gkrellm with lm-sensors installed. That will give you all the info you may ever need about your PC

---

### Post by polo_step on 2005-07-24
[QUOTE=jasmuz]Gkrellm with lm-sensors installed. That will give you all the info you may ever need about your PC[/QUOTE]
Interesting program!

I installed gkrellm and installed lm-sensors, but gkrellm doesn't see them and they don't show up in the GUI plugin list either, nor is it explained how they're to be used in man gkrellm.

I'm doing something wrong, here, right?  ;-)

---

### Post by polo_step on 2005-07-24
I also noticed when rebooting after installing this, in the bootup, there's now a 

setting sensors limits -- [FAIL] 

[sigh!]

---

### Post by polo_step on 2005-07-24
Apparently the very common chipset:  

SiS741GX-NB & SiS964L-SB

...are NOT SUPPORTED.

At least they do not appear to be listed on the lm-sensors page.

In-freakin'-credible...

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=polo_step]Apparently the very common chipset:  

SiS741GX-NB & SiS964L-SB

...are NOT SUPPORTED.

At least they do not appear to be listed on the lm-sensors page.

In-freakin'-credible...[/QUOTE]

Yeah...I can't get my chipset very much like that do allow for DMA. And usually SiS stuff works great with Linux. you take the good with the bad I guess.

---

