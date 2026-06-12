---
title: "Can't Change CPU Frequency"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-11-17
Hi

I'm running Dapper on my Celeron M machine.
I've finally got powernowd to work after adding this line : p4_clockmod into /etc/modules. But the daemon controls my cpu frequencies automatically. It has 8 available frequency with the lowest 187 Mhz. The daemon keeps scaling the frequencies every second and this is really annoying. CPU Frequency Scaling Monitor applet only let me see the current frequency but not to control the frequency. How do I control the frequency manually? I've read the help file and it shows that the frequencies can be controlled using the applet.

---

### Post by adam.tropics on 2006-11-18
try...


```
 sudo chmod +s /usr/bin/cpufreq-selector
```

---

### Post by junglepeanut on 2006-11-18
Also you could look at this:(kinda old)

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by TheTux on 2006-11-18
Thanks. That really help.

---

