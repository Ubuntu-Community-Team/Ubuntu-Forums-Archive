---
title: "lm-sensors"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-03-26
I installed lm-sensors from this tutorial here.
[http://ubuntuforums.org/showthread.php?t=2780&highlight=i2c+install](http://ubuntuforums.org/showthread.php?t=2780&highlight=i2c+install)

I am very excited because this is the first time I've been able to get an actual reading of the computer's temperature since first booting Linux, no other tutorials worked.

Adapter: SMBus I801 adapter at 1880
+2.5V:     +0.00 V  (min =  +3.32 V, max =  +3.32 V)   ALARM
VCore:     +0.00 V  (min =  +2.99 V, max =  +2.99 V)   ALARM
+3.3V:     +0.00 V  (min =  +4.38 V, max =  +4.11 V)   ALARM
+5V:       +0.00 V  (min =  +6.54 V, max =  +6.64 V)   ALARM
+12V:      +3.06 V  (min = +15.94 V, max = +15.94 V)   ALARM
VCC:       +3.33 V  (min =  +4.38 V, max =  +4.38 V)   ALARM
+1.5V:     +0.03 V  (min =  +1.99 V, max =  +1.49 V)   ALARM
+1.8V:     +0.00 V  (min =  +2.39 V, max =  +2.39 V)   ALARM
Chip Temp: +46.0°C  (low  =    -1°C, high =    -3°C)  ALARM
CPU Temp:  +83.0°C  (low  =    -5°C, high =    -1°C)
Sys Temp: -128.0°C  (low  =    -1°C, high =    -1°C)  FAULT
vid:      +1.475 V  (VRM Version 9.0)

(I havn't rebooted yet; I assume that's why Sys Temp isn't working)
Now.. how do I have the fan turn on; in my computer, when CPU Temp reaches above a certain temperature?

Is there a way to do this?
(also; how do I simply turn on my fan in the terminal?  Just to test to see if the fan CAN be turned on in Linux.)

Thank you for all of your help!

---

### Post by Brendantb on 2007-03-26
I am not sure of the specs of the machine on which you are working, but if you look in /proc/acpi you will find a "fan" directory, but also a directory with the brand of your machine, in which there is a "fan" command.  

For example, my computer is a Toshiba. Changing directory to /proc/acpi/toshiba lists the "fan" command. 

To turn my fan on, I have to be root: 

sudo su

Then the code to force on the fan:

echo "force_on:1" > /proc/acpi/toshiba/fan

If you look in /proc/acpi files you should be able to figure out your own path to the fan command.

---

### Post by chris062689 on 2007-03-26
I looked around in that folder..
chris@kubuntu:/proc/acpi$ dir
ac_adapter  button               event  info            sleep         video
alarm       dsdt                 fadt   power_resource  sony          wakeup
battery     embedded_controller  fan    processor       thermal_zone  wmi

All I saw was fan, which was a directory.
In that directory was FAN1 (also a folder.)
I only have one main fan (attached to the heatsink) that I want to turn on, I assume this is the one.

chris@kubuntu:/proc/acpi/fan/FAN1$ dir
state

state seems to be some kind of text file? (in nano all it had was status:  on)
Which the fan never runs; so I don't see how it think's it's on.

I tried echoing various things to it, and nothing changed (it still had status:  on)
Help? :(

---

### Post by chris062689 on 2007-03-26
I can't figure out how to turn on FAN1.  It says it's on but no fan is running.
Also; I've been digging around...
chris@kubuntu:~/Desktop$ acpi -t
     Thermal 1: passive active[0], 4294967040.0 degrees C
(this is in dmsg)
[   39.184093] pcc_acpi: loading...
[   44.484425] ppdev: user-space parallel port driver
[   46.455516] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   46.455524] apm: overridden by ACPI.
[   48.685847] [drm] Initialized drm 1.1.0 20060810
[   48.698272] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ                                     16


chris@kubuntu:~/Desktop$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.


hris@kubuntu:~/Desktop$ sudo ./cpufreq-detect.sh
This processor "Intel(R) Celeron(R) CPU 2.70GHz" is known _not_ to support power
-saving.


Any of this information helpful? :(

---

### Post by Brendantb on 2007-03-26
Hi, 

what is the output of:

./sony

when you are in the /proc/acpi directory?

---

### Post by chris062689 on 2007-03-26
That's also an empty folder.

---

### Post by chris062689 on 2007-03-26
Does anyone know how to enable my fan?  :confused:

---

### Post by chris062689 on 2007-03-27
Anyone know how to fix this problem? :(

---

### Post by chris062689 on 2007-03-30
Anyone figured this out?

---

