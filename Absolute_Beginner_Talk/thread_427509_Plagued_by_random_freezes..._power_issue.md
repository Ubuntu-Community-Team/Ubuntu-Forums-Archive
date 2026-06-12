---
title: "Plagued by random freezes... power issue?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by scott_g on 2007-04-29
I know there have been a few other posts about random lockups, but this is more specific, I think....

I have a HPa1610n computer (4200+ AMD processor, 1 GB Ram, 250GB SATA HD, 40GB IDE HD etc), and have added an Nvidia 7600GS card.  The box of the card recommends a 350 Watt power supply, although I have been using it with the stock 230 Watt PSU that came with the computer.  Every 2 hours or so, the computer locks up, especially when doing something that is video related (rendering, capturing, heavy beryl usage).  

These lockups occur in windows as well (except they're more frequent... like every 15 minutes or so)

So my question is: are my lockups due to an inadequate PSU?  or is there a tweak I'm missing?  

I tried adding: acpi=off noapic nolapic to my kernel boot options, but my comp froze on the login screen :( .

I can post anything that is required.

Thank you a lot for your help,
Scott

---

### Post by viciouslime on 2007-04-29
It is almost certainly the PSU yes. That's a lot of equipment to run off 230W, it'll be fine when idling, but when it is all drawing full power a 230W PSU will not manage it. I would suggest a decent  400W+ for such a system. Don't go for something cheap you'll only regret it when it doesn't perform any better than your current 230W one. :)

---

### Post by scott_g on 2007-06-06
Thanks for the reply,

Sorry, its been a while since I've read this thread (I've been busy lately); the lockups seem to occur less and less frequently now; almost once every two weeks or less.  I'd still likely get better performance from a better PSU (more $ = better experience).

As another note: Ubuntu runs better than windows; in windows, whenever I click on a video file, or change a video setting, the screen blanks out for a few seconds (I think this is because the graphics card is starved for power?), yet this doesn't happen in Ubuntu :D.

Scott

---

### Post by lazyart on 2007-06-06
You risk damaging your components with a too-small power supply.

---

### Post by Crafty Kisses on 2007-06-06
> **scott_g said:**
> Thanks for the reply,

Sorry, its been a while since I've read this thread (I've been busy lately); the lockups seem to occur less and less frequently now; almost once every two weeks or less.  I'd still likely get better performance from a better PSU (more $ = better experience).

As another note: Ubuntu runs better than windows; in windows, whenever I click on a video file, or change a video setting, the screen blanks out for a few seconds (I think this is because the graphics card is starved for power?), yet this doesn't happen in Ubuntu :D.

Scott

I reccomened you get a bigger power supply fast.

---

### Post by tgalati4 on 2007-06-06
Get a multimeter, plug the leads into a spare harddisk power lead.  Black to black and the red probe to either the red or yellow power lead.  Watch the voltage values (either 5V or 12V) during use.  If the voltage dips by more than 5% during video use, then your power supply is not adequate.

You can also install lm-sensors (sudo apt-get install lm-sensors) and display your voltages on your panel to see what is going on.

Good luck.

---

### Post by phr0ze on 2007-06-06
> **tgalati4 said:**
> You can also install lm-sensors (sudo apt-get install lm-sensors) and display your voltages on your panel to see what is going on.

Good luck.

I would use the software solution before resorting to the multimeter... Although it can be more hands on with a multimeter there is more risk to your computer and you if you probe the wrong areas.

---

### Post by scott_g on 2007-06-06
How can I get it to display the voltages?  I have lm-sensors installed, but so far, it only displayes CPU temperatures (I followed a tutorial in the Ubuntu Wiki).

Thanks,
Scott

---

### Post by tgalati4 on 2007-06-07
As a general rule of thumb, if you can see voltages in your BIOS then you can usually read them with lm-sensors.  If your BIOS doesn't display voltages, then it's 50/50 as to whether lm-sensors will pick them up.  Not all motherboards include the necessary monitoring chips to display system voltages.

Motherboards that can overclock, that can change bus speed, that can handle a large number of processors usually contain voltage monitors because voltages will change depending on what processor or what overclocking is used.

If you add some gnome panel applets sometimes they will pick up the voltage sensors discovered by lm-sensors.

This is what mine looks like:

tgalati4@hpubuntu:~$ sensors
adt7463-i2c-0-2e
Adapter: SMBus I801 adapter at fc00
V1.5:      +0.010 V  (min =  +1.42 V, max =  +1.58 V)   ALARM
VCore:     +1.330 V  (min =  +1.28 V, max =  +1.42 V)   
V3.3:      +3.313 V  (min =  +3.13 V, max =  +3.47 V)   
V5:       +5.221 V  (min =  +4.74 V, max =  +5.26 V)   
V12:      +12.600 V  (min = +12.60 V, max = +12.60 V)   ALARM
CPU_Fan:      0 RPM  (min = 4000 RPM)                     ALARM
fan2:         0 RPM  (min =    0 RPM)                     
fan3:         0 RPM  (min =    0 RPM)                     
fan4:         0 RPM  (min =    0 RPM)                     
CPU:      +34.50Â°C  (low  =  -128Â°C, high =   +50Â°C)       
Board:    +42.25Â°C  (low  =   +10Â°C, high =   +35Â°C)     ALARM 
Remote:   +46.00Â°C  (low  =   +10Â°C, high =   +35Â°C)     ALARM  
CPU_PWM:     1
Fan2_PWM:  255
Fan3_PWM:  255
vid:      +1.350 V  (VRM Version 9.1)

What is your output of:

sensors

If you can't get the internal voltages, then use a multimeter.

---

### Post by scott_g on 2007-06-07
I don't believe that my sensors will output voltages; I will post the output when I get home.

Thanks,
Scott

---

### Post by scott_g on 2007-06-07
Here is the output of sensors:

```

scott@scott-ubuntu:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +18°C
Core1 Temp:
             +30°C


```

I dont' think that has any voltages in it.  Any other options besides the multimeter?

Thanks,
Scott

---

### Post by tgalati4 on 2007-06-08
AMD users will have to chime in.  Explore all the nooks and crannies of the lm-sensors.org site.    All of my cpus/MOBO's are Intel.  A $10 multimeter can tell you if you need to upgrade to a $100 power supply.

The good news is that your temperatures look good.

---

### Post by scott_g on 2007-06-08
Ok,

I have a few multimeters, and will try this after exams in about 2 weeks :D.  

Anyone know why the temperature of core1 is always 10 degrees lower than the temperature of core2?

Thanks again,
Scott

---

