---
title: "speedstep-centrino"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-18
to enable my Freq scaling for my Intel Core 2.

i been told to enter this:

```
 sudo modprobe speedstep-centrino 
```

i always get this error and do not know why

```
 scott@scott-desktop:~$ sudo modprobe speedstep-centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-16-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy 
```

anyone know why?

---

### Post by Bachstelze on 2007-06-18
speedstep-centrino is deprecated in 2.6.20, you should modprobe acpi-cpufreq instead.

And if it still doesn't work, that means your CPU is not supported.


EDIT : by the look of this error message, it seems acpi-cpufreq is already loaded, you can check it with the *lsmod* command. If that's the case, you can go ahead and configure your freq scaling.

---

### Post by skymera on 2007-06-18
ive got apci-cpufreq.

but with my mums laptop, she could adjust her performance from 50% to 0ver 100%
i can get from 1.6GHz eacgh core to 1.87GHz each core. :S

---

### Post by Bachstelze on 2007-06-18
Afraid I can't help you much further 'cause I'm not very familiar with how Ubuntu handles cpu freq scaling. With cpufreqd in Slack, I can also adjust my frequency from 50% to 100%.

---

### Post by skymera on 2007-06-18
mines 85% min and go to 1.87GHz, from 1.86GHz.
0.01GHz in crease :S

---

