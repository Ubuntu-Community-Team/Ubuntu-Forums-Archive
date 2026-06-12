---
title: "Cpu-Scaling Wont Go below 1.4 Ghz? Whats Wrong?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2007-08-07
Hey guys, I have a centrino M, 1.8 ghz, and it will only go as low as 1.4 ghz for some strange reason.

```

 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
600000 800000 1000000 1200000 1400000 1600000 1800000 

sudo cpufreq-selector -f 600000

```

It should work, but its only reading 1.4 Ghz in the scaling applet.

Thanks in advance

---

### Post by milosz.galazka on 2007-08-07
Hello, did you looked at these links:
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

---

