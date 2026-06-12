---
title: "CPU frequency &quot;gets stuck&quot; at the lowest setting after laptop wakes up"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by softtower on 2007-09-09
I have ThinkPad T60p with Core 2 Duo 2Gz CPU.
 
When the laptop wakes up after sleeping in standby mode, my CPU frequency gets stuck in the lowest possible mode: 1Gz. I know that this is CPU frequency scaling module who's doing that. I tried to change many different variables: running on AC power vs battery, switching between governors (ondemand, conservative) - nothing helps. It wakes up and does not scale from 1Gz. (I know how to force CPU go up to 2Gz even with conservative governor - I run several instances of glxgears).

Below is the output from cpufreq-info, as you can see it says *"frequency should be within 1000 MHz and 1000 MHz"*. It correctly reports hardware max. limit of 2GHz, but **cpufreq thinks that the upper allowed frequency limit is only 1Gz**!!!

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, performance
  current policy: frequency should be within 1000 MHz and 1000 MHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz (asserted by call to hardware).

```

If I reboot everything goes back to normal. CPU scales up and the output above says "should be withtin 1000 MHz and 2 GHz".

I have been trying to fix it myself. For instance I added the following to /etc/default/acpi-support (trying to reload CPU scaling kernel modules on suspend/resume):
```
MODULES="cpufreq_stats cpufreq_conservative acpi-cpufreq"
```

It did not help. 
Then I tried 
```
sudo cpufreq-set -u 2000000
or
sudo cpufreq-set -u 2GHz
```
Those did not do anything either - CPU still could not get up to 2Gz.

Also I wet to /sys/devices/system/cpu and run these commands as root:

```
echo 2000000 > cpu0/cpufreq/scaling_max_freq
echo 2000000 > cpu1/cpufreq/scaling_max_freq

```

... and nothing happens. Those two files still say 1000000. Normally (after reboot) they report 2000000 and I can write other values into them. At this point I am not sure what else can I try. Obviously I should update wakeup/resume scripts with some commands to bitch-slap cpu frequency scaling module, but I cannot figure out what to do.

Here is my /etc/default/cpufrequtils
```
ENABLE="true"
GOVERNOR="conservative"
MIN_SPEED=1000000
MAX_SPEED=2000000

```

Here is my /etc/modules
```
lp

cpufreq_stats
cpufreq_ondemand
cpufreq_conservative
cpufreq_powersave
acpi-cpufreq  # this is what Core 2 Duo needs. 

fuse

```

This is very frustrating. I spent 5 hours last night trying to figure this out...

---

### Post by softtower on 2007-09-09
This is very possible a bug, that was reported here (you'll have to scroll down since bug title is misleading):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/124797](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/124797)

---

