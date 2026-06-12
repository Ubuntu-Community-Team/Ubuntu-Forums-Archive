---
title: "Gkrellm and adding to what info it shows?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-19
I have installed Gkrellm, lm-sensors, x86-info,Gkrellmapcupsd, hdmon and gkrellm-hdplop.

If I type 'sensors' in the Terminal, I get this---

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +37°C

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.44 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +1.66 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.36 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +5.05 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.22 V  (min =  +0.00 V, max = +16.32 V)   
-12V:     -15.33 V  (min = -27.36 V, max =  +3.93 V)   
-5V:       -0.20 V  (min = -13.64 V, max =  +4.03 V)   
Stdby:     +5.05 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +3.04 V
fan1:        0 RPM  (min =  811 RPM, div = 8)          
fan2:        0 RPM  (min =  811 RPM, div = 8)          
fan3:        0 RPM  (min =  811 RPM, div = 8)          
M/B Temp:    +30°C  (low  =  +127°C, high =  +127°C)   sensor = diode   
CPU Temp:    +36°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
Temp3:       +31°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor 

How can I get this info shown in Gkrellm please?

Currently, Gkrellm displys this info only--

[[IMG]http://img180.imageshack.us/img180/5664/screenshotgkrellmen9.png[/IMG]](http://imageshack.us)

---

### Post by spiderbatdad on 2007-12-19
i take it you found all the gkrellm plugins in synaptic? after starting gkrellm right click on it in an open area and use the configuration tool to navigate through builtins and plugins, selecting the ones you want.

---

### Post by MangasColoradas on 2007-12-19
Yep, I installed all that were relevant looking from synaptic. There are some, like 'screenshot' plugins etc, I didnt bother with.

---

### Post by SOULRiDER on 2007-12-19
I suggest you try out Conky, IMHO its far better than gkrellm. Theres a nice htread in the how to forum with lots of scripts and examples.

---

### Post by spiderbatdad on 2007-12-19
IMHO conky is not far better than gkrellm.

---

### Post by MangasColoradas on 2007-12-19
Thanks Soulrider I will have a look at Conky.

Gkrellm crashes when I add hdplop or apcupsd. But I am seeing HD info and cpu speed info anyway.

When I go to 'built ins' and 'sensors' there is nothing there, except in the options it mentions hdmon daemon port.

---

### Post by MangasColoradas on 2007-12-19
Also, in 'sensors-info' it says this

Setup
Enter data scaling factors and offsets for the sensors if the default
values are not correct for your motherboard.  Do a man gkrellm or
see the GKrellM README for more information.
Enter a zero factor and a blank label to restore default values.

Drag and drop sensor rows to change the displayed order.

Temperature offset values must be in centigrade units.

Substitution variables may be used in alert commands.
	$s    current sensor value.
	$l    sensor label.

---

### Post by MangasColoradas on 2007-12-19
Conky is described as 'highly configurable' but I cant see how to do that as yet.

Its not showing the stuff I want as it is now, anyway.

Some Gkrellm info

 Sensor monitoring on Linux requires that either lm_sensors modules  are
       installed  in  your  running  kernel, that you run a kernel >= 2.6 with
       sysfs sensors configured, or, for i386 architectures, that you have the
       mbmon  daemon  running when gkrellm is started.  If the mbmon daemon is
       used, it must be started before gkrellm like so:

              mbmon -r -P port-number

       where the given "port-number"  must  be  configured  to  match  in  the
       gkrellm  Sensors->Options config.  Sensor temperatures can also be read
       from /proc/acpi/thermal_zone, /proc/acpi/thermal,  /proc/acpi/ibm,  the
       PowerMac  Windfarm /sysfs interface, and PowerMac PMU /sysfs based sen&#8208;
       sors.

       When using lm_sensors, libsensors will be used  if  available,  but  if
       libsensors is not linked into the program, the sensor data will be read
       directly from the /sysfs or /proc file systems.   If  running  a  newer
       Linux  kernel sensor module not yet supported by libsensors and libsen&#8208;
       sors is linked, there will also be  an  automaitc   fallback  to  using
       /sysfs  as  long  as  libsensors doesn&#8217;t detect any sensors.  But if it
       does detect some sensors which does not include  the  new  sensors  you
       need, you can force getting /sysfs sensor data either by running:
 gkrellm --without-libsensors





I have libsensors but  'gkrellm --without-libsensors' doesnt help.

---

### Post by MangasColoradas on 2007-12-19
I am gonna use sensors-applet for temps for now! ;)

I have it in my taskbar.

---

