---
title: "macbook pro 8,2 oneirc sensor TCTD at 255degrees?"
date: 2012-01-23
forum: Apple Hardware Users
---

### Post by zulumonkey on 2012-01-23
Hey,

I've got the following output from "sensors" - coretemp is inside my /etc/modules and I've got macfanctl installed.

> applesmc-isa-0300
Adapter: ISA adapter
Left side  : 4274 RPM  (min = 4366 RPM)
Right side : 4274 RPM  (min = 4366 RPM)
TB0T:         +33.8°C  
TB1T:         +33.8°C  
TB2T:         +32.5°C  
TC0C:         +60.2°C  
TC0D:         +59.0°C  
TC0E:         +63.5°C  
TC0F:         +64.8°C  
TC0P:         +52.8°C  
TC1C:         +61.0°C  
TC2C:         +62.0°C  
TC3C:         +61.0°C  
TC4C:         +61.0°C  
TCFC:          +0.0°C  
TCGC:         +61.0°C  
TCSA:         +56.0°C  
TCTD:        +255.8°C  
TG0D:         +54.2°C  
TG0P:         +54.0°C  
THSP:         +43.0°C  
TM0S:         +57.5°C  
TMBS:          +0.0°C  
TP0P:         +56.5°C  
TPCD:         +61.0°C  
TW0P:        +129.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +65.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +62.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +61.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +65.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +59.0°C  (high = +86.0°C, crit = +100.0°C)

As you can see I've got TCTD running at 255 degrees, this surely cannot be a good sign. What on earth is this sensor reading?

Also this TW0P module which is wireless airport from my findings, is running extremely high too.

Anyone got more accurate names for these?

With the default setup of having the min fan speed at 2000RPM I had the fans running quiet for about 15 seconds, then at full blast (5500RPM) for another 10 seconds so I tweaked them to run at 3000RPM at bare minimum.  Anyone else run into the issue I mentioned previously?

cheers

---

### Post by DocteurX on 2012-01-23
I'm also running oneiric on Macbook pro 8,2. 

I just ran [FONT=Courier New]sensors[/FONT] twice in the last 2 minutes and got this :

```

$sensors
[...]
applesmc-isa-0300
Adapter: ISA adapter
Left side  : 2002 RPM  (min = 2000 RPM)
Right side : 2002 RPM  (min = 2000 RPM)

[...]
TCTD:        +255.8°C  
[...]

$ sensors
[...]
applesmc-isa-0300
Adapter: ISA adapter
Left side  : 1998 RPM  (min = 2000 RPM)
Right side : 2001 RPM  (min = 2000 RPM)
[...]  
TCTD:          +0.0°C  
[...]

```The TCTD sensor is clearly meaningless. Also, the fans run at ~2000 RMP almost all the time, it get higher only when I use a lot of cpu. I would suggest to start by installing cpu usage and frequency indicators (like [FONT=Courier New]indicator-sysmonitor[/FONT] and [FONT=Courier New]indicator-cpufreq[/FONT]) to see if your CPU usage is normal. If they're not, use [FONT=Courier New]top[/FONT] to see who is eating the CPU !

---

