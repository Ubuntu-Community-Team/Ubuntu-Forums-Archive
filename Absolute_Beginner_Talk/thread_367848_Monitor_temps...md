---
title: "Monitor temps.."
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by makko on 2007-02-22
Hi,
I have just rearranged the cooling setup for my CPU.. and I have relocated my PSU in the case..
Is there any software out there that will monitor the CPU temperature and possibly the PSU temperature and record the highs and lows over time.. and generate reports..

I will need to know how hot it's going to be getting because it will be a server when fully functional..

Thanks,

makko

---

### Post by mysticrider92 on 2007-02-22
[Here]("http://linux.softpedia.com/get/System/Monitoring/Hardware-Monitor-3711.shtml") is a temperature monitor for Linux that I just found. It won't give you the PSU temperature, but it will do everything else. You should probably search Synaptic before installing anything from the internet so that there are no conflicts.

---

### Post by nickoli_02 on 2007-02-22
I think you will be pretty hard pressed to find any sort of PSU temp monitor. I'm pretty sure most power supplies don't have software available temp monitors anyway. I wouldn't worry about it as long as you have a good quality PSU.

---

### Post by kinematic on 2007-02-22
lmsensors works great.
just follow the setup routine and afterwards install sensors-applet.

---

### Post by makko on 2007-02-22
This wis what I got from lm-sensor, I wonder are these temps ok..
Q's should I have the alarm enabled,how? Also, what does High and hyst mean??

Thanks...

w83782d-i2c-0-2d
Adapter: SMBus AMD756 adapter at 50e0
VCore 1:   +1.60 V  (min =  +1.54 V, max =  +1.70 V)
VCore 2:   +3.34 V  (min =  +1.54 V, max =  +1.70 V)       ALARM
+3.3V:     +3.33 V  (min =  +3.14 V, max =  +3.46 V)
+5V:       +4.87 V  (min =  +4.73 V, max =  +5.24 V)
+12V:     +11.98 V  (min = +10.82 V, max = +13.19 V)
-12V:     -11.78 V  (min = -13.18 V, max = -10.88 V)
-5V:       -5.15 V  (min =  -5.25 V, max =  -4.75 V)
V5SB:      +4.95 V  (min =  +4.73 V, max =  +5.24 V)
VBat:      +3.02 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 2657 RPM, div = 2)
fan2:        0 RPM  (min = 2657 RPM, div = 2)
fan3:        0 RPM  (min =  664 RPM, div = 8)
temp1:       +21°C  (high =   +16°C, hyst =   -94°C)   sensor = thermistor 
temp2:     +26.0°C  (high =   +62°C, hyst =   +60°C)   sensor = thermistor 
temp3:    +127.5°C  (high =   +80°C, hyst =   +75°C)   sensor = diode   ALARM
vid:      +1.625 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm disabled

---

