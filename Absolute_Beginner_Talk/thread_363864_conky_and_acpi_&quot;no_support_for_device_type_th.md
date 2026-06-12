---
title: "conky and acpi: &quot;no support for device type: thermal&quot;"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by nmsmith on 2007-02-17
I've been trying to get conky to display my cpu temp and hdd temp. I followed a useful thread for the hddtemp but the cpu seems to work pretty trouble free for most people, thus little mention of it on the threads. However for me Conky just reports "0".

So I try the following:
```
nick@cloanthus:~$ acpi -V
No support for device type: thermal
```

and:
```
nick@cloanthus:~$ ls /proc/acpi/thermal_zone/ -lah
total 0
dr-xr-xr-x  2 root root 0 2007-02-17 19:12 .
dr-xr-xr-x 14 root root 0 2007-02-17 12:16 ..
```

I tried lm-sensors and I get:
```
nick@cloanthus:~$ sensors
w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.07 V  (min =  +1.71 V, max =  +1.89 V)       ALARM  
+3.3V:     +3.17 V  (min =  +3.14 V, max =  +3.47 V)              
+5V:       +5.00 V  (min =  +4.76 V, max =  +5.24 V)              
+12V:     +11.25 V  (min = +10.82 V, max = +13.19 V)              
-12V:      +0.30 V  (min = -13.18 V, max = -10.80 V)       ALARM  
-5V:       +1.63 V  (min =  -5.25 V, max =  -4.75 V)       ALARM  
V5SB:      +5.38 V  (min =  +4.76 V, max =  +5.24 V)       ALARM  
VBat:      +0.00 V  (min =  +2.40 V, max =  +3.60 V)       ALARM  
fan1:        0 RPM  (min =    0 RPM, div = 8)                     
fan2:        0 RPM  (min =    0 RPM, div = 8)                     
temp1:       +35°C  (high =    -1°C, hyst =    -1°C)   sensor = thermistor   ALARM   
temp2:     +30.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
alarms:   
beep_enable:
          Sound alarm enabled
```

So the sensors are indeed there, and they report to the gnome sensors-applet, but I'd rather have everything in conky as it's more configurable and doesn't take up valuable gnome-panel space.

So what's wrong with my ACPI?

PS on another note I have only just discovered that in conky using a dual core processor CPU0 refers to the whole thang, while CPU1 and CPU2 refer to the individual cores. Is this documented anywhere?

---

### Post by energiya on 2007-02-18
you could try i2c

> 
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or
#                                    temp/tempf (first in C, second in F)
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.           


```

CPU: ${i2c 0-002d temp 2}

```

This was taken from [here]("http://conky.sourceforge.net/conkyrc-citi"). Visit [this]("http://conky.sourceforge.net/screenshots.html") and [this]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky") pages for more configs.

---

### Post by nmsmith on 2007-02-18
Thanks Energiya, that worked brilliantly. Now I just have to work out which temps temp 1 and temp 2 are. I feel a few cpu tests coming on . . .

---

### Post by energiya on 2007-02-18
> **nmsmith said:**
> Now I just have to work out which temps temp 1 and temp 2 are. I feel a few cpu tests coming on . . .

Just make your CPU suffer for a few minutes and you will find out witch is witch. Your lm_sensors output is a little confusing to me because I'm used to at least 3 temperatures... and a more explicit output. For example, I have:
> 
M/B Temp:    +31°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
CPU Temp:    +15°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
Temp3:       +17°C  (low  =  +127°C, high =  +127°C)   sensor = diode   

Temp3 being the HDD.

And... nice screen you got there :)

---

