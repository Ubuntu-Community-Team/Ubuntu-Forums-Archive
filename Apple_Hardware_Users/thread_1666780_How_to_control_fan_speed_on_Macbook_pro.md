---
title: "How to control fan speed on Macbook pro?"
date: 2011-01-14
forum: Apple Hardware Users
---

### Post by ste.sancri on 2011-01-14
Hi! My MBP 5.3 is running quite hot all the time with 10.04 Lucid  (this is what I get when I run 'sensors' command) 

```

stefano@stefano-laptop:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +58.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (high = +105.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Left side  :1999 RPM  (min = 2000 RPM)
Right side :2001 RPM  (min = 2000 RPM)
temp1:       +43.0°C                                    
temp2:       +43.0°C                                    
temp3:       +38.8°C                                    
temp4:        +0.0°C                                    
temp5:       +59.5°C                                    
temp6:       +52.5°C                                    
temp7:       +55.0°C                                    
temp8:       +64.0°C                                    
temp9:       +59.2°C                                    
temp10:      +49.2°C                                    
temp11:      +58.8°C                                    
temp12:      +59.0°C                                    
ERROR: Can't get value of subfeature temp13_input: I/O error
temp13:       +0.0°C                                    
temp14:      +60.2°C                                    
temp15:      +58.0°C                                    
temp16:      +49.0°C                                    
temp17:      +52.0°C                                    
temp18:      +60.5°C                                    
temp19:      +36.0°C                                    
temp20:      +46.0°C                                    

stefano@stefano-laptop:~$ 

```Is there a way to decide fan speed?!

I tried this tutorial [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480) but I cannot manage it to work

Thank you!

---

### Post by teejmya on 2011-01-14
Here's what I did to fix that:

[http://ubuntuforums.org/showpost.php?p=10246215&postcount=6](http://ubuntuforums.org/showpost.php?p=10246215&postcount=6)

---

### Post by ste.sancri on 2011-01-14
Wow thank you very much! That worked for me! 

I've also paste
```
echo $1 > /sys/devices/platform/applesmc.768/fan2_min
```

Into the fan.sh file in order to get also the other fan working like the other.

Thank you very much for your help!

---

### Post by ste.sancri on 2011-01-14
Wow thank you very much! That worked for me! 

I've also paste
```
echo $1 > /sys/devices/platform/applesmc.768/fan2_min
```

Into the fan.sh file in order to get also the other fan working like the other.

Thank you very much for your help!

---

