---
title: "Fan control on MacPro4,1"
date: 2012-11-30
forum: Apple Hardware Users
---

### Post by wrotte on 2012-11-30
Hi folks - 

I am trying to get 12.04 LTS Server on my MacPro4,1 workstation and have had some success.  One particular bone of contention that I have been having is with the fan control.  

I have installed the applesmc-dkms and macfanctld packages from the mactel-support ppa.  While macfanctld does cause the fans to run, it appears to make them run at jet engine speed unconditionally.  After looking at the macfanctld log, I see that it is not at all detecting any of my temperature sensors:

```

$ cat /var/log/macfanctl.log 
Using parameters:
	temp_avg_floor: 45
	temp_avg_ceiling: 55
	temp_TC0P_floor: 50
	temp_TC0P_ceiling: 58
	temp_TG0P_floor: 50
	temp_TG0P_ceiling: 58
	fan_min: 2000
	log_level: 0
Found applesmc at /sys/devices/platform/applesmc.768
Found 2 fans.
Found 75 sensors:
Error: Can't read  /sys/devices/platform/applesmc.768/temp63_label
	 1: TA0P - ? 
	 2: TCAC - ? 
	 3: TCAD - ? 
	 4: TCAG - ? 
.... continuing ad nauseam

```

A couple observations:

1)  It is only detecting 2 fans, whereas lm_sensors detects 6.  
2)  It is not successfully reading from any of the sensors.  

My guess would be that since it can't read any of the sensors, it is running the fans a full tilt as a safety measure.  

Note that lm_sensors does appear to work:

```


$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +54.0°C  (high = +85.0°C, crit = +95.0°C)
Core 1:       +51.0°C  (high = +85.0°C, crit = +95.0°C)
Core 2:       +53.0°C  (high = +85.0°C, crit = +95.0°C)
Core 3:       +51.0°C  (high = +85.0°C, crit = +95.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 0:       +47.0°C  (high = +85.0°C, crit = +95.0°C)
Core 1:       +46.0°C  (high = +85.0°C, crit = +95.0°C)
Core 2:       +47.0°C  (high = +85.0°C, crit = +95.0°C)
Core 3:       +44.0°C  (high = +85.0°C, crit = +95.0°C)

nouveau-pci-0500
Adapter: PCI adapter
temp1:        +54.0°C  (high = +100.0°C, crit = +110.0°C)

applesmc-isa-0300
Adapter: ISA adapter
PCI :        4520 RPM  (min = 4629 RPM)
PS :         2727 RPM  (min = 4629 RPM)
EXHAUST :     599 RPM  (min =  600 RPM)
INTAKE :      600 RPM  (min =  600 RPM)
BOOSTA :     1345 RPM  (min =  800 RPM)
BOOSTB :     1112 RPM  (min =  800 RPM)
TA0P:         +28.5°C  
TCAC:         +40.5°C  
.... continuing ad nauseam

```

Does anyone have suggestions as to how I might get macfanctl to work correctly, or alternative fan control strategies that I might use so that I don't have to wear protective headgear whilst working on my workstation?

thanks,
/-Will

---

### Post by 2F4U on 2012-11-30
Seems as if macfanctl is also causing problems for other people.

[http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431)

This post is a bit dated, but it may still contain valuable information.

---

### Post by gotofbi on 2013-05-08
This post is kinda outdated but I am having same issue but can not find solution.
Link from 2F4U does not help to resolve fan problem on MacPro4,1

How can I solve this fan issue?

I want to use Mac Pro as server machine but without working fan, I am very scared.

I am using MacPro4,1 (Quad core W3520) + ubuntu-12.04.2-server-amd64

---

