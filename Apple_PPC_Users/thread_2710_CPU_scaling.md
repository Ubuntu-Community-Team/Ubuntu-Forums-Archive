---
title: "CPU scaling"
date: 2004-10-30
forum: Apple PPC Users
---

### Post by khc on 2004-10-30
According to the hardware support page cpu scaling is supported. but it doesn't work here. I have a 867MHz TiBook and it's always running at 667MHz

---

### Post by SyL on 2004-10-31
The CPU speed various with the needs.
  
  Look at :  [b]/sys/devices/system/cpu/cpu0/cpufreq
  [/b]there is a lot of interessing information :
  ```

  root@oZ:/sys/devices/system/cpu/cpu0/cpufreq # cat cpuinfo_max_freq
  1333333
  root@oZ:/sys/devices/system/cpu/cpu0/cpufreq # cat cpuinfo_min_freq
  666666
  
``` 
  
 So, the speed change automatically in function of needs. For check that works, try to run many greedy processes and cat /proc/cpuinfo
  
  But you can control it yourself :
   ```
echo -n "1000000" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
``` 
  That will set it to 1 Ghz.
  
  
  Hope that help

---

### Post by khc on 2004-10-31
That's way cool, thanks!

---

### Post by TekMate on 2005-01-22
Is there a way to set this permently?

---

### Post by Viro on 2005-01-24
[QUOTE=TekMate]Is there a way to set this permently?[/QUOTE]
 Put that line in the file .gnomerc in your home directory.

---

