---
title: "Understand the difference between the CPU History and CPU Frequency Scaling Monitors?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-18
RE: Understand the difference between the CPU History and CPU Frequency Scaling Monitors?

I would like to understand the difference between the CPU History Monitor and CPU Frequency Scaling Monitor.

I have a AMD 64 Athlon X2 and kernel-release 2.6.12-10-386.

The CPU History Monitor acts as expected, when I do something I see spikes... That's normal.

The CPU Frequency Scaling Monitor always displays "Userspace 2GHz (100%)".

So, from what I understand, The CPU governor is set to Userspace and performance runs the CPU at max-frequency?

Is this a bad thing?

I just don't want to fry any thing today...

Thanks,

tpatrick:/sys/devices/system/cpu/cpu0/cpufreq$ cat scaling_available_frequencies
2000000 1800000 1000000

tpatrick:/sys/devices/system/cpu/cpu0/cpufreq$ cat scaling_available_governors
userspace powersave ondemand conservative performance

tpatrick:/sys/devices/system/cpu/cpu0/cpufreq$ sudo powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 1000Mhz - 2000Mhz (3 steps)

---

### Post by Ramses de Norre on 2006-03-18
The CPU History Monitor shows how many of the cpu's capacity to calculate is used.

The CPU Frequency Scaling Monitor shows at which frequency your cpu is running. On a normal desktop you'll want it to be 100%. By setting a lower frequency you'll underclock your cpu, which is done sometime on notebooks when they're not used heavily, to get a longer batterylife.

---

### Post by jtp51 on 2006-03-18
Ramses de Norre: thank you very much for clarifying this topic.

---

