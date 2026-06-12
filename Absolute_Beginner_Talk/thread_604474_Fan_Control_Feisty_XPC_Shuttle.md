---
title: "Fan Control Feisty XPC Shuttle"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by axgopala on 2007-11-06
Hi,

The fan in the desktop is always switched on.

I've read all the posts about fan control earlier and have installed lm-sensors and tried using the fancontrol script given at: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

it doesnt work. I get the following output from sensors:

[root@holst ~]$ sensors
it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.15 V  (min =  +0.00 V, max =  +3.82 V)
VCore 2:   +1.50 V  (min =  +4.02 V, max =  +4.08 V)   ALARM
+3.3V:     +3.30 V  (min =  +2.99 V, max =  +3.95 V)
+5V:       +5.19 V  (min =  +0.00 V, max =  +6.64 V)
+12V:     +11.97 V  (min =  +0.00 V, max = +16.32 V)
-12V:      +3.93 V  (min =  -0.24 V, max =  +3.93 V)   ALARM
-5V:       -5.88 V  (min =  +3.89 V, max =  -0.41 V)   ALARM
Stdby:     +5.16 V  (min =  +5.99 V, max =  +6.85 V)   ALARM
VBat:      +3.28 V
fan1:        0 RPM  (min =    0 RPM, div = 8 )
fan2:        0 RPM  (min =    0 RPM, div = 8 )
fan3:        0 RPM  (min =    0 RPM, div = 8 )
M/B Temp:    -55°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor
CPU Temp:    -55°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor
Temp3:       -55°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor

Somehow its not able to detect the RPM of the fan at all. I have a dual processor PC, the XPC shuttle that is a dual boot with windows and Ubuntu 7.04

Any help is appreciated.

Thanks

Anandha

---

### Post by gn2 on 2007-11-06
Get a Zalman Fanmate or an Akasa Junior?

---

### Post by axgopala on 2007-11-06
Thanks

---

