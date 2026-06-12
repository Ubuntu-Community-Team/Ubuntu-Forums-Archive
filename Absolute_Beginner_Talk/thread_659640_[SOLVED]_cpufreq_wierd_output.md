---
title: "[SOLVED] cpufreq wierd output"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by whitethorn on 2008-01-05
I was trying to figure out how to get cpufreq to work on my laptop,  I have a dell inspiron 8600 with a 1.5 Mhz M processor,  in my bios I have Speedstep enabled,  I followed a couple howto here on site 

[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

I can click around on the gnome applet cpu monitor thingy on the desktop, but nothing really happens, and when I change the governors using cpufreq-selector -g ***  conservative or powersave and when I run  cpufreq-info  I get this

 cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.50 GHz
  available frequency steps: 1.50 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: userspace, ondemand, powersave, conservative, performance
  current policy: frequency should be within 1.50 GHz and 1.50 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz.

Although it says I can change the frequency to the different steps, in each governor I can go from 1.5 Ghz to 1.5 Ghz.  Ne ideas?  Or is there any way to write my own governor? Oh and when I change the governor using the terminal the change shows up on my desktop.  I have also gotten rid of powernowd

---

### Post by dcstar on 2008-01-06
> **whitethorn said:**
> I was trying to figure out how to get cpufreq to work on my laptop,  I have a dell inspiron 8600 with a 1.5 Mhz M processor,  in my bios I have Speedstep enabled,  I followed a couple howto here on site 

[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

I can click around on the gnome applet cpu monitor thingy on the desktop, but nothing really happens, and when I change the governors using cpufreq-selector -g ***  conservative or powersave and when I run  cpufreq-info  I get this

 cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.50 GHz
  available frequency steps: 1.50 GHz, 1.20 GHz, 1000 MHz, 800 MHz, 600 MHz
  available cpufreq governors: userspace, ondemand, powersave, conservative, performance
  current policy: frequency should be within 1.50 GHz and 1.50 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz.

Although it says I can change the frequency to the different steps, in each governor I can go from 1.5 Ghz to 1.5 Ghz.  Ne ideas?  Or is there any way to write my own governor? Oh and when I change the governor using the terminal the change shows up on my desktop.  I have also gotten rid of powernowd

Here is mine (on an AMD 64 CPU):
```
root@dc-desktop:/home/dc# cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, ondemand, powersave, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).
analyzing CPU 1:[B]
  driver: powernow-k8[/B]
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: userspace, ondemand, powersave, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).
```
I can change things with the applet icon, and as you can see I am using a specific driver and not the generic ACPI one.

---

### Post by Bachstelze on 2008-01-06
@whitethorn

```
current policy: frequency should be within 1.50 GHz and 1.50 GHz.
```

You can change the upper and lower limits with *cpufreq-set -u* and *cpufreq-set -d*, respectively. For example :

```
sudo cpufreq-set -d 600
```

Should set the lower limit to 600 MHz. Of course, you can't just type anything you want, you must use one of the listed frequencies your processor supports.


@dcstar, *powernow-k8* is the driver for AMD CPUs based on the K8 architecture, it obviously won't work on an Intel and *acpi-cpufreq* is the right one to use on Speedstep CPUs.

---

### Post by whitethorn on 2008-01-06
Hi Guys

Thanx for the help, I played around with it a little more tried out a couple things you guys wrote, and now it works.  

But unfortunately when I change the cpufreq using the terminal, it works, What I mean is I can use the plugin to change the cpu freq, but then after a while it just goes back to performance mode and it doesn't all me to change anything, and then I need to back into the terminal, and change it to another governor and reset the top and bottom cpu freq
using

cpufreq-set -u

Is there a way to get it to stay it won't go switch to performance on it's own?  I hope this makes sense

---

