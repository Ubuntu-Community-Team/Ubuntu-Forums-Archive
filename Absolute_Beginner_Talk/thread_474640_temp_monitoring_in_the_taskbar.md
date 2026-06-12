---
title: "temp monitoring in the taskbar?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-06-15
i cannot for the life of me remember what its  called nor where to find it.i don't want gdesklets i want a taskbar monitor showing my temps of cpu/mobo etc? you know the kind.
but what one? i cannot remember.i'm sure there various ones but i wouldn't know what terms to search under.
sorry to be a pain.

---

### Post by ushills on 2007-06-15
I installed xsensors and then has the option when clicking on the taskbar to add system monitoring. Then selected temperatures, cpu and memory, these now show in the taskbar.

---

### Post by ramjet_1953 on 2007-06-15
To have  applets in the taskbar for temperature monitoring do the following:
It's a two-step process, as you need to get the SMART monitoring package for your HDD.

1.[COLOR="Red"] sudo apt-get install hddtemp[/COLOR]
When it installs, it will ask if you want it to start monitoring on startup, click the yes box. Also it will also ask some questions about ports and ip addresses,  just accept the defaults.

2. [COLOR="Red"]sudo apt-get install sensors-applet[/COLOR]
This will then be added to the applets available when you right-click on either the top or bottom panel.
When you right click on the panel, choose [COLOR="Blue"]Add to Panel[/COLOR] and then choose [COLOR="Blue"]Hardware Sensors Monitor.[/COLOR]

You then need to work through the config of your sensors and make sure that the ones you want have a tick in the box next to them.

Regards,
Roger :cool:

---

### Post by keef247 on 2007-06-27
> **ramjet_1953 said:**
> To have  applets in the taskbar for temperature monitoring do the following:
It's a two-step process, as you need to get the SMART monitoring package for your HDD.

1.[COLOR="Red"] sudo apt-get install hhdtemp[/COLOR]
When it installs, it will ask if you want it to start monitoring on startup, click the yes box. Also it will also ask some questions about ports and ip addresses,  just accept the defaults.

2. [COLOR="Red"]sudo apt-get install sensors-applet[/COLOR]
This will then be added to the applets available when you right-click on either the top or bottom panel.
When you right click on the panel, choose [COLOR="Blue"]Add to Panel[/COLOR] and then choose [COLOR="Blue"]Hardware Sensors Monitor.[/COLOR]

You then need to work through the config of your sensors and make sure that the ones you want have a tick in the box next to them.

Regards,
Roger :cool:
its only giving me hdd temp options.i need to monitor cpu/motherboard.how do i do this?

---

### Post by aks44 on 2007-06-27
The **lm-sensors** back-end provides CPU & motherboard temperature monitoring.

As a front-end I use **KSensors** which is pretty nice if you are using KDE.

---

### Post by PCFascist on 2007-06-27
For those running xubuntu or xfce I suggest the **xfce4-sensors-plugin**, via apt-get.
It will require lm-sensors and works with hddtemp if you choose to install it.

---

### Post by bodhi.zazen on 2007-06-27
This is a gem of a post as well : [http://ubuntuforums.org/showpost.php?&p=2468147&postcount=24](http://ubuntuforums.org/showpost.php?&p=2468147&postcount=24)

*Thanks ayenack*

---

### Post by keef247 on 2007-06-28
working nice now.strange though i have one reading at 47c which is what it is according to the asus software in windows but i also have one at 57c!!!! which is what the motherboard tells me it is... So I'm pretty unsure and worried which temp is right as I don't really want 57c of heat on my cpu!...

---

### Post by keef247 on 2007-06-28
everything is ok dontworry:D

---

### Post by dptxp on 2007-06-28
How do I display cpu temperature on my desktop ?

---

### Post by bodhi.zazen on 2007-06-28
> **dptxp said:**
> How do I display cpu temperature on my desktop ?

Threads merged. Look up ^^

---

### Post by Seisen on 2007-06-28
> **bodhi.zazen said:**
> Threads merged. Look up ^^

Are you having fun merging threads?

---

### Post by oldsmobile_mike on 2008-03-04
Thanks, ramjet_1953!  This solution worked perfectly for me!  I can now add cpu temp & hard drive temp to my taskbar.:KS


> **ramjet_1953 said:**
> To have  applets in the taskbar for temperature monitoring do the following:
It's a two-step process, as you need to get the SMART monitoring package for your HDD.

1.[COLOR="Red"] sudo apt-get install hddtemp[/COLOR]
When it installs, it will ask if you want it to start monitoring on startup, click the yes box. Also it will also ask some questions about ports and ip addresses,  just accept the defaults.

2. [COLOR="Red"]sudo apt-get install sensors-applet[/COLOR]
This will then be added to the applets available when you right-click on either the top or bottom panel.
When you right click on the panel, choose [COLOR="Blue"]Add to Panel[/COLOR] and then choose [COLOR="Blue"]Hardware Sensors Monitor.[/COLOR]

You then need to work through the config of your sensors and make sure that the ones you want have a tick in the box next to them.

Regards,
Roger :cool:

---

### Post by RichTJ99 on 2008-03-11
My sensor options are hddtemp or acpi.  Are either of those the CPU?

---

### Post by glennric on 2008-03-11
ACPI is the cpu.  

You can also install computertemp.  It is another applet for the panel.  I didn't know about the sensors-applet.  That one is nicer.

---

### Post by oldsmobile_mike on 2008-03-12
> **RichTJ99 said:**
> My sensor options are hddtemp or acpi.  Are either of those the CPU?

ACPI is not the CPU, it's the power supply, or the system power management bus, and (at least in my experience) not very useful to know the temperature of.  I've monitored ACPI temperatures in the past using utilities like SpeedFan (Windows), and it's never changed or given me any relevant information related to actual temperatures within the PC.

Sources:

[http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)
[http://www.helpwithpcs.com/jargon/acpi.htm](http://www.helpwithpcs.com/jargon/acpi.htm)
[http://linux.about.com/cs/linux101/g/ACPI.htm](http://linux.about.com/cs/linux101/g/ACPI.htm)
[http://forums.majorgeeks.com/showthread.php?t=91155](http://forums.majorgeeks.com/showthread.php?t=91155)

And hddtemp is the hard drive temperature, obviously.

It's possible you have a Dell PC, or another model that doesn't report the system CPU temp.  Not much you can do about it other than try a different motherboard, unfortunately.  :(

---

### Post by glennric on 2008-03-12
> **oldsmobile_mike said:**
> ACPI is not the CPU, it's the power supply, or the system power management bus, and (at least in my experience) not very useful to know the temperature of.  I've monitored ACPI temperatures in the past using utilities like SpeedFan (Windows), and it's never changed or given me any relevant information related to actual temperatures within the PC.

Sources:

[http://en.wikipedia.org/wiki/ACPI](http://en.wikipedia.org/wiki/ACPI)
[http://www.helpwithpcs.com/jargon/acpi.htm](http://www.helpwithpcs.com/jargon/acpi.htm)
[http://linux.about.com/cs/linux101/g/ACPI.htm](http://linux.about.com/cs/linux101/g/ACPI.htm)
[http://forums.majorgeeks.com/showthread.php?t=91155](http://forums.majorgeeks.com/showthread.php?t=91155)

And hddtemp is the hard drive temperature, obviously.

It's possible you have a Dell PC, or another model that doesn't report the system CPU temp.  Not much you can do about it other than try a different motherboard, unfortunately.  :(

Typing "acpi -v" gives the temperature of your cpu.  This is what the acpi option of the sensors-applet returns as well.

---

### Post by dccrens on 2008-04-28
I am using lm-sensors and it works great. I just installed computertemp so I can display temps in the gnome panel. It works, however, the font display next to the icon is black so with a black or transparent panel, you can't see the read out. Does anyone know if you can change the font color? I have tried researching through the developer website but not much there...

---

### Post by slick_nick on 2008-04-30
Wow my temps are all in the single-digits in degrees Celsius :)  Guess that's what happens with a Cooler Master case and not having overclocked anything yet!

---

