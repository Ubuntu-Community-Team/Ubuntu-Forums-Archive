---
title: "cpufreq: cannot switch to ondemand/conservative governor"
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by chimaera on 2009-08-25
Hi, 

on my 12" PB I cannot seem to get cpufreq working properly. Using the vanilla installation, there was no frequency scaling taking place at all. After installing powernowd, I get auto-scaling, can switch the two available frequencies manually (userspace) or use the performance/powersave governors. The ondemand and conservative governors, however, are not working. 

The appropriate governors seem to be available: 
```
~$ sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance

```

The modules are loaded and on trying to switch to ondemand/conservative I get the following: 
```
ondemand governor failed, too long transition latency of HW, fallback to performance governor

```

This is no pressing issue, for userspace is working using powernowd, but I would like to know the reason for the strange behaviour anyway. Any hints?

---

### Post by FactTech on 2010-06-22
Take a look at the following bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706)

It may be helpful in identifying the specific problem.

---

