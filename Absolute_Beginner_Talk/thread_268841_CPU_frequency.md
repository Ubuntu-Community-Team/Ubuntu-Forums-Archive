---
title: "CPU frequency"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-09-30
I've got ubuntu installed in a pc which has a Sempron 3100 +. The frequency of this CPU is 1800 MHz. When I installed gdesklets, I see that cpu is running at 1004,66 MHz. Why is not running at 1800? How can I change it?

---

### Post by madmetal on 2006-09-30
amd cool 'n' quiet which is something good..
reduced frequency >> reduced power consumption and temperature..

---

### Post by kinematic on 2006-09-30
ubuntu uses the powernow daemon to regulate the frequency of your cpu.
when it's idle it's scaled down to 1ghz and when the load is high it goes up to 1,8ghz.
if you right click somewhere in a spot of empty space on the panel and select  
add to panel there's a cpu applet in the list.
if you add that you can see the scaling in real time.

---

### Post by Nrvnqsr on 2006-09-30
type this in your terminal

> 
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies


if your it give you numbers like "1800000" "1000000" and possibly another numerical value then you processor supports AMD's Cool and Quiet which trottles down if your CPU is idle and trottles up if its processing alot of info


but if you want to manually change its power you can type this in the terminal

> 
sudo chmod +s /usr/bin/cpufreq-selector


and right-click and "Add to panel" place "CPU Frequency Monitor on the panel and left-click on the it will give you some governors "userspace "powersave" "on demand" "conservative" "performance" and applies either low power usage to maximum performance respectively. 

To me, its very cool when I'm on my laptop and I want to minimize my power useage while I'm not connected to a AC adapter

---

