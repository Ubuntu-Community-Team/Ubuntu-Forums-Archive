---
title: "Is my CPU cooking?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Erdaron on 2007-07-08
So my concern stems from my CPU fan being really loud. It's not excessive, but definitely noticeable. In the past, this has been a sign of it dying.

My other concern is that the CPU is running hot. I'm not overclocking it, but while transferring it between motherboards, the heatsink came off. I reattached it with some thermal contact grease, but I'm not sure that it's quality contact, so I'm wondering if it's not cooling efficiently, and the fan is so loud because it's maxing out its speed.

The CPU is an AMD Atholon XP 2400+ running at 2GHz.

Is there an app that would allow me to monitor CPU temperature, and what kind of values are considered "normal"?

---

### Post by isaacj87 on 2007-07-08
Yup, there is a CPU temp applet you can install.

Do this:

Goto System->Administration->Synaptic and do a search for sensors-applet, install it

Then right click on the panel and choose "add to panel"

From the new window, in the "System & Hardware" category choose "Hardware Sensors Monitor"

Hope this is what you were looking for!

For you question about normal temps...Anything under 60 C is okay...I have a laptop with a laptop cooler pad that idles around 30-40 C and when I'm working the CPU it goes up to about 55-60 C.

---

### Post by Vajra Vrtti on 2007-07-08
First, you have to [install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780").
Then, GNOME Sensors Applet (package **sensors-applet**) is a good tool to monitor lm-sensors data.

---

### Post by Erdaron on 2007-07-09
Simply installing the sensors-applet seems to have worked. The CPU is sitting at 40C. I guess this fan doesn't have much left in it, then.

Thanks gents!

---

### Post by DrMega on 2007-07-09
> **Erdaron said:**
> Simply installing the sensors-applet seems to have worked. The CPU is sitting at 40C. I guess this fan doesn't have much left in it, then.

Thanks gents!

40C is well within acceptable limits. On a warm summer day, in doors, it could get into the 30's without even being switched on, just because of the ambient temperature.

Maybe your fan is on its way out but for now it is still cooling. Another thing that can sound like a fan failing, but is actually more serious is a hard disk failing. Sometimes they can sound really loud, getting steadily louder as they approach failure. Unless you can definately pin the noise down to the CPU fan, I would be doing some hasty backups about now.

---

### Post by Wiebelhaus on 2007-07-09
just replace the heatsink man , cheap as hell now.

---

### Post by Vajra Vrtti on 2007-07-09
> Another thing that can sound like a fan failing, but is actually more serious is a hard disk failing.
Another interesting tool is [hddtemp]("http://www.guzu.net/linux/hddtemp.php"). People forget disks get hot too. But use with care, it has already caused me some  [problems]("https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/117621").
Its results can also be displayed in the GNOME Sensors Applet .

---

### Post by laidback on 2007-07-09
Recently installed a new fan on my Athlon XP socket A system which was making a dreadful noise. Bought an item from Ebuyer (UK online shopping outlet), Akasa AK-786 Socket A CPU Cooler at a silly price. Cleaned heatsink and fan at the same time, the noise difference is fantastic, from unbearable to very tolerable. I did it as an experiment and I'm very pleased with the result.

---

### Post by Erdaron on 2007-08-03
Hm. At first, I just installed sensors-applet, and that's what was showing 40C. However, this number never changes, which made me suspicious. So I went through the steps in [this thread]("http://ubuntuforums.org/showthread.php?t=2780") to install lm-sensors.

Running *sensors* in terminal gave me this output:

```
it87-isa-0290
Adapter: ISA adapter
VCore 1:   +1.60 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +3.26 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +2.93 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +5.00 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:      +8.26 V  (min =  +0.00 V, max = +16.32 V)   
-12V:     -17.42 V  (min = -27.36 V, max =  +3.93 V)   
-5V:       -9.48 V  (min = -13.64 V, max =  +4.03 V)   
Stdby:     +2.34 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +0.00 V
fan1:     4687 RPM  (min =    0 RPM, div = 8)          
fan2:     2057 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +79°C  (low  =  +127°C, high =   +90°C)   sensor = diode   
CPU Temp:     +0°C  (low  =  +127°C, high =   +90°C)   sensor = disabled   
Temp3:        +0°C  (low  =  +127°C, high =   +90°C)   sensor = disabled   

```

Why is my CPU sensor disabled, and why does it look like my motherboard is about to burst into flames?

---

### Post by Vajra Vrtti on 2007-08-03
Are you sure your CPU does have a temperature sensor?

This are my readings:
[FONT="Courier New"]> w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.54 V  (min =  +0.00 V, max =  +3.84 V)              
+12V:     +11.92 V  (min =  +0.61 V, max = +12.89 V)              
+3.3V:     +3.33 V  (min =  +0.74 V, max =  +2.80 V)       ALARM  
+5V:       +4.99 V  (min =  +1.73 V, max =  +2.40 V)       ALARM  
-12V:      +0.47 V  (min =  +1.37 V, max = -13.59 V)       ALARM  
V5SB:      +5.03 V  (min =  +0.65 V, max =  +3.20 V)       ALARM  
VBat:      +1.70 V  (min =  +3.06 V, max =  +0.83 V)       ALARM  
fan1:     2250 RPM  (min = 168750 RPM, div = 4)              ALARM  
CPU Fan:  2721 RPM  (min = 168750 RPM, div = 4)              ALARM  
fan3:        0 RPM  (min = 6750 RPM, div = 2)              ALARM  
M/B Temp:    +31°C  (high =   +81°C, hyst =    +9°C)   sensor = thermistor           
CPU Temp:  +47.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
temp3:     +27.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
vid:      +1.525 V  (VRM Version 9.0)[/FONT]

---

### Post by Erdaron on 2007-08-03
Shouldn't there be a CPU thermal sensor? Is there any way I could check if it physically there?

And that seems awfully hot for the MB. Could scaling be off?

---

### Post by Rocket2DMn on 2007-08-03
The noise could be caused by fan friction.  Cleaning the fan and chassis should help, but if the fan continues working hard and making noise, it may need to be replaced.  40 degrees is definitely an acceptable temperature.  My laptop runs from 40-70, it's a Pentium M @ 2ghz, but it's a hot processor.

---

### Post by w4ett on 2007-08-03
40 degrees on a CPU is COOL........the old Athlon XP's with the stock AMD supplied fans run normally around 50 C........with better cooling my Athlon XP 2400 overclocked to 2.26 Ghz with a Thermaltake Silent Boost with Copper Heatsink runs at 40C at idle and 52C at load......Plus it's rated at 70C by AMD.

---

