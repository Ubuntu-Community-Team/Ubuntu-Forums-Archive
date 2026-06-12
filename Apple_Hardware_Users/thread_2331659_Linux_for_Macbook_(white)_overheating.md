---
title: "Linux for Macbook (white) overheating"
date: 2016-07-24
forum: Apple Hardware Users
---

### Post by h1cloud on 2016-07-24
Installed Xubuntu 16.04.1 on Macbook (white late 2008, core 2 duo, 2GB Ram), but there are overheating issues (heavy fan activity). 

OS observed until now:
-ubuntu 14.04.2
-ubuntu 10.10 
-xubuntu 16.04.1
(no overheating with OSX 10.6.8 / Snow Leopard)

Someone with same problem found a solution?

---

### Post by este.el.paz on 2016-07-25
Please read the sticky at the top of the page "Intel Macs" . . . should be instruction for adding "macfancntrol" or other options.

e..

---

### Post by h1cloud on 2016-07-25
a tool to "control" (=lower) high fan-freq when processor-temp is high
...makes no sense!?

this tool you mentioned is osx

---

### Post by MikeBraxner on 2016-07-30
@ h1cloud ... I don't have a 'white late 2008' MB, so I can only speculate.

Without a lot more information (power-consumption and temp readings, driver versioning, kernel version, ...), there's no way to be certain that your problem is a 'Linux caused' temperature issue, or possibly just a configuration problem with your fan control (as este.el.paz implicitly suggested) ... or a hardware issue, or ... 

If it's temperature, then there could be a variety of causes, first and foremost: Perception ... Linux is going to run hotter than OS X, period. Check the actual temperature. If its 'off' by just a couple of degrees, then its not a 'heat issue', but the result of hardware-specialized power-management by Apple, which your not likely to match.

Second, a while back people kept running into ACPI-interrupt storms on GPE66 and GPE4E (if I remember that correctly), you might want to check ...
```
grep . -r /sys/firmware/acpi/interrupts/
```
If necessary you can curtail those via /etc/rc.local
```
#!/bin/bash 
echo "disable" > /sys/firmware/acpi/interrupts/gpe66
echo "disable" > /sys/firmware/acpi/interrupts/gpe4E
```

Third--and this should go without saying--review and sort out your basic power management (ALPM, TLP, cpufreq, Wakeup events, Flash--yeah, I know, get rid of it---PowerTop, lmsensors, and-yes-macfanctld).

Finally, you might also want to reset your SMC, since this can at times resolve a slew of issues in one go ... and/or fry your install ;-)

Best of luck.

---

### Post by h1cloud on 2016-08-01
Hi Mike,

thanks for speculations and comments with further explanations in explicit sentenceS :)

In between I changed to Linux Mint 18 (+thermald) and its quite satisfying.
Temperature is still a little thing, so I will see if I can get any extra cooling from your comments.

Thanks!

I dont know if ther is any useful Information to extract from my Mint 18 interrupts !?

$ grep . -r /sys/firmware/acpi/interrupts/
/sys/firmware/acpi/interrupts/sci:   15631
/sys/firmware/acpi/interrupts/error:       0
/sys/firmware/acpi/interrupts/gpe00:       0   invalid
/sys/firmware/acpi/interrupts/gpe01:       0   enabled
/sys/firmware/acpi/interrupts/gpe02:       0   enabled
/sys/firmware/acpi/interrupts/gpe03:       0   disabled
/sys/firmware/acpi/interrupts/gpe04:       0   disabled
/sys/firmware/acpi/interrupts/gpe05:       0   invalid
/sys/firmware/acpi/interrupts/gpe06:       0   invalid
/sys/firmware/acpi/interrupts/gpe07:       0   enabled
/sys/firmware/acpi/interrupts/gpe08:       0   invalid
/sys/firmware/acpi/interrupts/gpe09:       0   disabled
/sys/firmware/acpi/interrupts/gpe10:       0   invalid
/sys/firmware/acpi/interrupts/gpe11:       0   enabled
/sys/firmware/acpi/interrupts/gpe12:       0   invalid
/sys/firmware/acpi/interrupts/gpe13:       0   invalid
/sys/firmware/acpi/interrupts/gpe14:       0   invalid
/sys/firmware/acpi/interrupts/gpe15:       0   invalid
/sys/firmware/acpi/interrupts/gpe16:       0   invalid
/sys/firmware/acpi/interrupts/gpe0A:       0   invalid
/sys/firmware/acpi/interrupts/gpe17:   15631   enabled
/sys/firmware/acpi/interrupts/gpe0B:       0   enabled
/sys/firmware/acpi/interrupts/gpe18:       0   invalid
/sys/firmware/acpi/interrupts/gpe0C:       0   disabled
/sys/firmware/acpi/interrupts/gpe19:       0   invalid
/sys/firmware/acpi/interrupts/gpe0D:       0   disabled
/sys/firmware/acpi/interrupts/gpe0E:       0   disabled
/sys/firmware/acpi/interrupts/gpe0F:       0   invalid
/sys/firmware/acpi/interrupts/gpe1A:       0   invalid
/sys/firmware/acpi/interrupts/gpe1B:       0   invalid
/sys/firmware/acpi/interrupts/gpe1C:       0   invalid
/sys/firmware/acpi/interrupts/gpe1D:       0   enabled
/sys/firmware/acpi/interrupts/gpe1E:       0   invalid
/sys/firmware/acpi/interrupts/gpe1F:       0   invalid
/sys/firmware/acpi/interrupts/sci_not:      18
/sys/firmware/acpi/interrupts/ff_pmtimer:       0   invalid
/sys/firmware/acpi/interrupts/ff_rt_clk:       0   disabled
/sys/firmware/acpi/interrupts/gpe_all:   15631
/sys/firmware/acpi/interrupts/ff_gbl_lock:       0   enabled
/sys/firmware/acpi/interrupts/ff_pwr_btn:       0   enabled
/sys/firmware/acpi/interrupts/ff_slp_btn:       0   invalid

---

### Post by MikeBraxner on 2016-08-01
> **h1cloud said:**
>  ... any useful Information to extract from my Mint 18 interrupts !?
...
/sys/firmware/acpi/interrupts/sci:   15631
...
/sys/firmware/acpi/interrupts/gpe17:   15631   enabled
.../sys/firmware/acpi/interrupts/gpe_all:   15631


The only one really active is scsi, so, no, nothing untoward here.

As for the rest, just ensure ... i.e. MAKE SURE, and DOUBLE CHECK, don't just 'ASSUME' ... that all your tools, settings, configs, etc., are properly installed, adjusted, conditioned, specified, ... 'apt-geting' a tool is not the same as installing a tool. 

Have fun, and keep smiling ... it helps with the pain.:-)

---

