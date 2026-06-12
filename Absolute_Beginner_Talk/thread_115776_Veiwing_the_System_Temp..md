---
title: "Veiwing the System Temp."
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by lgmdaniel on 2006-01-11
Whats the best way to view the system temp, I'm able to do this in my XP partition and via the system bios. But I'm unsure what tool I need to view this in Kubuntu. Its just I'm going to swap over a rather noisy fan and I need to keep a eye on the temps. At the moment in XP it runs at 50c on the CPU and 30c in the system, I would like to get it down to 35c on the CPU same as my Dad's PC.

---

### Post by KingBahamut on 2006-01-11
lmsensors most likely. 
[http://secure.netroedge.com/~lm78/](http://secure.netroedge.com/~lm78/)

---

### Post by lgmdaniel on 2006-01-14
I'm just looked at Ubunyu and it shows LM-snesors installed? Any one tell me where I have to look to get this running?

---

### Post by simber on 2006-01-14
this is what i did : 

all the credit goes to this thread : 

[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=cpu+temp](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=cpu+temp)

install lm-sensors

sudo apt-get install lm-sensors
 
then run sensors detect

sudo sensors-detect

it would ask you a lot of questions : just hit enter every time, until it asks if you want to add some lines to /etc/modules/ and type yes

then you can reload your modules by reeboting the pc or do what the thread  mentioned above says

now type sensors and it would display something like this :

it87-isa-0290
Adapter: ISA adapter
VCore 1: +1.57 V (min = +1.42 V, max = +1.57 V) ALARM
VCore 2: +2.66 V (min = +2.40 V, max = +2.61 V) ALARM
+3.3V: +6.59 V (min = +3.14 V, max = +3.46 V) ALARM
+5V: +5.11 V (min = +4.76 V, max = +5.24 V)
+12V: +11.78 V (min = +11.39 V, max = +12.61 V)
-12V: -19.14 V (min = -12.63 V, max = -11.41 V) ALARM
-5V: +0.77 V (min = -5.26 V, max = -4.77 V) ALARM
Stdby: +5.00 V (min = +4.76 V, max = +5.24 V)
VBat: +3.12 V
fan1: 3668 RPM (min = 0 RPM, div =
fan2: 0 RPM (min = 664 RPM, div = ALARM
fan3: 0 RPM (min = 2657 RPM, div = 2) ALARM
M/B Temp: +39°C (low = +15°C, high = +40°C) sensor = thermistor
CPU Temp: +36°C (low = +15°C, high = +45°C) sensor = thermistor
Temp3: +96°C (low = +15°C, high = +45°C) sensor = diode

now install sensors-applet 

sudo apt-get install sensors applet

right click your mouse over a panel and install the applet

it would show you the cpu and other temps.

sorry about my english

if u need more help let me know

---

### Post by lgmdaniel on 2006-01-20
Thanks, I've managed to get it all working now though not sensors applet, just seems to error about not finding a source package. I've had a look as I seem to have all the package links. So I'm a bit unsure now.

```
daniel@Grinch:~$ sensors
w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.78 V  (min =  +1.71 V, max =  +1.89 V)
+3.3V:     +3.31 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.92 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +12.40 V  (min = +10.82 V, max = +13.19 V)
-12V:     -12.28 V  (min = -13.18 V, max = -10.80 V)
-5V:       -5.35 V  (min =  -5.25 V, max =  -4.75 V)       ALARM
V5SB:      +5.59 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.49 V  (min =  +2.40 V, max =  +3.60 V)
fan1:     5037 RPM  (min = 9926 RPM, div = 2)
fan2:        0 RPM  (min = 2667 RPM, div = 2)
temp1:       +31°C  (high =   -17°C, hyst =   +62°C)   sensor = thermistor   ALARM
temp2:     +49.5°C  (high =   +75°C, hyst =   +72°C)   sensor = thermistor
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

daniel@Grinch:~$ sudo apt-get install sensors applet
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sensors
daniel@Grinch:~$

```

---

### Post by lgmdaniel on 2006-01-23
Ok. that problem has go away but now its telling me the sensors applet does not exsist....
```

daniel@Grinch:~$ sudo apt-get install sensors applet
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sensors
daniel@Grinch:~$    
```

Any chance of someone giving me the right name.. cheers.

---

### Post by Omnios on 2006-01-23
sensors-applet

---

### Post by kaamos on 2006-01-23
It's "sensors-applet".

---

### Post by Turin Turambar on 2006-02-01
I just installed & configured sensors. The temperature is ok, it's just that the labels are wrong. The temperature of MB is actually a CPU temp and vice versa. How can I change that?

---

### Post by lgmdaniel on 2006-02-03
[QUOTE=simber]
now install sensors-applet 

sudo apt-get install sensors applet

right click your mouse over a panel and install the applet

it would show you the cpu and other temps.

sorry about my english

if u need more help let me know[/QUOTE]
Sorry I've installed it.. but this last bit has confused me a little? Add what where?

---

