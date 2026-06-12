---
title: "Can't start powernowd"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-08-28
I tried the CPU Frequency scaling Howto and it didn't work for me. So I tried to reinstall powernowd. It is, however, replaced by powersaved. I need powernowd to have power top read frequency usage. However, I found the package online. Installed, but won't start. I now am left with a sloooooow laptop. 

Error from powernowd:
```
/sys/devices/system/cpu/cpu0/cpufreq/affected_cpus: No such file or directory
powernowd: err=2
powernowd: Found 1 scalable unit:  -- 2 'CPUs' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

```

I checked the cpu0, and their is no cpufreq directory.

HELP!

---

### Post by st33med on 2007-08-28
OK, reinstalled powersaved, it runs faster now. But I really REALLY want powernowd to run again.

---

### Post by reset3x on 2007-08-28
are you positive your cpu supports this?

---

### Post by st33med on 2007-08-28
positive. I have speedstep in BIOS, everything worked before. I even had that cpufreq directory. Don't know what happened to it after that reboot.

---

### Post by st33med on 2007-08-29
Bump

---

