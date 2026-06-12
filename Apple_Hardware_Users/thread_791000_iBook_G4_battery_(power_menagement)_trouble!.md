---
title: "iBook G4 battery (power menagement) trouble!"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by cyber_brain_mfkg on 2008-05-11
hi all! i have iBook G4 (1.42GHz ppc,512MB RAM, 60GB hdd, ati FireGL Mobility T2e...etc)

every works fine except my battery lasts for about an hour instead of 2,5-3 as it was in ubuntu 7.10!

for some reasons i had to uninstall ubuntu 7.10 and i decided to install 8.04!
As i remember well i installed something in 7.10 that drastic prolonged battery life!

I've tried everything i found...:
1. tried both ACPI and APM
2. installed laptop-mode-tools
3. powertop
4. tried powernowd,dyncpu,pmud,pmud-utils,pbbuttons,pommed....

but no success at all!!!Has anyone any sugestion!
thanks

---

### Post by stream303 on 2008-05-12
I'd check to see if frequency-scaling is working.  Can you install a cpu-freq monitoring applet or when the system seems idle, do a

```
cat /proc/cpuinfo
```

With Hardy, I found that for some reason, powernowd is not working and is installed by default.  In my case, I had to uninstall powernowd, and install CPUDYN instead to get some sort of cpu frequency scaling working.

---

