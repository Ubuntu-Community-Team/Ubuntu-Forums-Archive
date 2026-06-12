---
title: "powernowd"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Talisker on 2006-08-05
Hi

I installed Dapper on my AMD mobile64 Athlon Laptop. Everything runs great so far.
I was wondering about Powernowd. Synaptic Package Manager listed Powernowd version 0.97 as installed.

Is there a more suitable driver, or is this one just fine?
Also, is there a program that would allow me to monitor CPU speed and voltage? Kinda like CPU-z in Windows?

Thanks.

---

### Post by tkiesel on 2006-08-05
Hi Talisker,

If you're applying updates regularly as they appear in the update manager icon, then your installation of powernowd is fully updated. :D 


To watch frequency scaling in action, add the CPU Frequency Scaling Monitor to your upper or lower panel.  Right click on the panel, choose "Add to Panel" and select the CPU Frequency Scaling Monitor.  Voila! You can see your CPU's clock frequency in real time.  You can right click the applet and adjust the appearance of the information to suit you.

I'd be using that applet myself if the motherboard I purchased supported frequency scaling.  (I wish it did, but it was a freebie with the processor from NewEgg, so I can't complain that much.)

For voltage and temperature readings you'll want to install sensors-applet (which you can put on your panel just like the CPU Frequency Scaling Monitor) and lm-sensors. (the package that actually manages your motherboard sensors)

First thing to do there is to do some reading on this forum about correctly configuring lm-sensors.

Good luck!
-T

---

### Post by Talisker on 2006-08-05
Hi Tkiesel

Great Info...... that's what I was looking for. I didn't know about the add in the Toolbar....

Thanks!

---

