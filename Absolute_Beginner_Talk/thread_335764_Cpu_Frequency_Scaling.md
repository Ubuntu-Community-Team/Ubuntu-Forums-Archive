---
title: "Cpu Frequency Scaling"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2007-01-10
Im using gnome-applet to do this but its limited to changing the speeds from 1GHz to 2GHz. Can I go any lower? Thanks!

---

### Post by qamelian on 2007-01-10
> **nyxynyx said:**
> Im using gnome-applet to do this but its limited to changing the speeds from 1GHz to 2GHz. Can I go any lower? Thanks!

It depends on your CPU. Mine switches between 1.6 and 2.4 Ghz. There's only a limited range for scaling.

---

### Post by Ptero-4 on 2007-01-10
It depends on your processor, some may not give accurate ranges and confuse the hell off the CPU frequency monitor applet.

---

### Post by Ocxic on 2007-01-10
"cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies"

this will give you the amount of differnet scaling frequency's your cpu will give you.

---

### Post by simonn on 2007-01-10
It depends on the capabilities of you cpu.

The below will give you some insight.

```

$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq

```

---

### Post by Atomic Dog on 2007-01-10
My guess would be that 1ghz is your minimum.

---

### Post by nyxynyx on 2007-01-10
Ic, thanks for the replies! Are there any utilities to underclock the CPU? I remembered playing with one that can adjust the cpu clock speed after booting into the OS but its only available in windows. Or can I disable 1 core?

---

### Post by %hMa@?b&lt;C on 2007-01-10
why does the processor not display overcloced speeds?

---

### Post by maddog39 on 2007-01-10
Well, I have PowerPC G4 and I can only scale like 100Mhz back, which kinda sucks but yea.

This doesnt work btw(or atleast not on my CPU/comp, I get 'file not found.'):
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

```

---

