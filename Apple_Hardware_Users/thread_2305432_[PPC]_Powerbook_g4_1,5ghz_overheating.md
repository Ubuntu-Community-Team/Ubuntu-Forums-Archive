---
title: "[PPC] Powerbook g4 1,5ghz overheating"
date: 2015-12-05
forum: Apple Hardware Users
---

### Post by jayme3 on 2015-12-05
Hello everyone!

I had successfully installed xubuntu 11.04 on my powerbook g4, everything worked, except for the fact that it overheated.

0) in 11.04 fan didn't worked at first
1) i loaded [COLOR=#333333][FONT=monospace]therm_adt746x module - no success [/FONT]
[FONT=monospace]2) installed lm_sensors and fan control - did not detected any sensors on both them, found [/FONT][this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1353005")[FONT=monospace] thread describing the same issue saying it might be the kernel [/FONT]
[FONT=monospace]3) downloaded 12.04 formatted again and upgraded to 11.04, kept the old kernel and ran it - no success, the fan worked, however it overheated again as it didn't come up to often[/FONT]
[FONT=monospace]4) figured out how i could adjust /sys/devices/temperatures/limit_adjuster to -15 and added to rc.local file - i got the fan running more often and louder now, but still overheats. [/FONT]

[FONT=monospace]anyone knows how to prevent overheating? [/FONT]
[FONT=monospace]thank you all in advance [/FONT][/COLOR]

---

### Post by rican-linux on 2015-12-08
take a looks at **[this]("https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F")**.

---

