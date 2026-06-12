---
title: "MacBook Pro 9,2 Overheat issue"
date: 2013-08-12
forum: Apple Hardware Users
---

### Post by bustamanteguevara on 2013-08-12
Hi, I have been wondering in many forums now, but none of them has the information specific to this computer (MacBook Pro 9,2). 

I noticed that the area above the computer got consideraby hotter when I run ubuntu, as opposed to OsX. So, here begins the search: 

[B]To get a reading of the temperature you need to install lm-sensors
[/B]
taken from [http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431)

1. install lm-sensors: sudo apt-get install lm-sensors
2. configure the sensors and add to /etc/modules, in terminal run:  sensors-detect, answer yes to all questions, once finished searching all  the sensors are sensors cpu will come out and ask them if they want to  add them to /etc/modules RESPOND YES
example:
#---- Cut here ----
CoreTemp
LM75 (lm75 can change in your macbook, so use the your its only example)
#---- Cut here ----
ask if you want to automatically add them to /etc/modules, respond YES

You can also look for info here.
[http://lm-sensors.org/wiki/FAQ/Chapter2](http://lm-sensors.org/wiki/FAQ/Chapter2)

To probe the computers temperature you need to type "sensors" 

[B] The driver that cools the computer using the fan better is 
[/B]
***[COLOR=#000000][FONT=Arial]macfanctld[/FONT][/COLOR]***

to get it you need to type

sudo apt-get install macfanctld

The temperature reduces considerably:

Before instalation it was 

sensors
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   6203 RPM  (min = 6200 RPM)
TA0P:         +51.2°C  
TB0T:         +37.5°C  
TB1T:         +37.2°C  
TB2T:         +37.5°C  
TC0E:         +91.5°C  
TC0F:         +92.2°C  
TC0J:          +0.8°C  
TC0P:         +72.2°C  
TC1C:         +86.0°C  
TC2C:         +91.0°C  
TCFC:          +0.0°C  
TCGC:         +82.0°C  
TCSA:         +81.0°C  
TCTD:          +0.0°C  
TCXC:         +92.0°C  
TG1D:         +92.2°C  
TM0P:         +46.8°C  
TM0S:         +51.5°C  
TPCD:         +73.0°C  
Th1H:         +56.2°C  
Ts0P:         +35.2°C  
Ts0S:         +49.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +92.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +86.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +92.0°C  (high = +87.0°C, crit = +105.0°C)


15 mins after instalation it was


MacBookPro:~$ sensors
applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :   4199 RPM  (min = 5665 RPM)
TA0P:         +47.0°C  
TB0T:         +38.0°C  
TB1T:         +38.0°C  
TB2T:         +37.5°C  
TC0E:         +67.8°C  
TC0F:         +70.0°C  
TC0J:          +2.0°C  
TC0P:         +54.8°C  
TC1C:         +64.0°C  
TC2C:         +64.0°C  
TCFC:          +0.0°C  
TCGC:         +64.0°C  
TCSA:         +55.0°C  
TCTD:        +255.8°C  
TCXC:         +64.8°C  
TG1D:         +70.0°C  
TM0P:         +44.2°C  
TM0S:         +49.2°C  
TPCD:         +66.0°C  
Th1H:         +47.2°C  
Ts0P:         +35.2°C  
Ts0S:         +43.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +66.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +64.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +66.0°C  (high = +87.0°C, crit = +105.0°C)



However, the fans are sort of oscilating, they go from high power to low sort of fast. This forum says that the issues in many models have already been adressed,  [http://ubuntuforums.org/showthread.php?t=1467062&highlight=cpu+temperature](http://ubuntuforums.org/showthread.php?t=1467062&highlight=cpu+temperature), but they are hard for the newcomer to find. That is true, I can't find something specific for my Mac. 

So please, if anybody knows about this, post it here. 

Other questions I have:

Is there a command that plots the temperature as a function of time in lm_sensors? 
what are the best practices to reduce power consumption?

Thank you all for contributing!

---

