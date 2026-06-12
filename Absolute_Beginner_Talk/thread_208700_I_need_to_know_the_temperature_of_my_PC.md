---
title: "I need to know the temperature of my PC"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-04
what program should I use ? (don't want to use the bios).

---

### Post by scxtt on 2006-07-04
lm-sensors and/or (x)mbmon and/or hddtemp, all in the repos ...

---

### Post by chajuram on 2006-07-04
Hi

I am sorry, I wanted to delete this messege but could not figure out how.

---

### Post by confused57 on 2006-07-04
[QUOTE=MAXDDARK]what program should I use ? (don't want to use the bios).[/QUOTE]
You can use Synaptic Package Manager to install:
gkrellm
lm-sensors

You'll need to configure lm-sensors using this guide:
[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

If your bios has an option for displaying temperatures of your cpu, zone temps, and fan speeds, then it should support the use of lm-sensors.

---

### Post by MaximB on 2006-07-04
thanx..I'll try thouse

---

### Post by nanotube on 2006-07-04
you could also try sensors-applet (i use it, it's great :) ).

---

### Post by MaximB on 2006-07-04
[QUOTE=nanotube]you could also try sensors-applet (i use it, it's great :) ).[/QUOTE]

I've installed this package - but I do not see it...were is it ? (I've checked applications and system and couldn't find it).

---

### Post by ProjectGod on 2006-07-04
do a search for it...

**whereis sensors-applet**

or

**which -a sensors-applet**

or if it all fails... search

/bin, or /usr/bin, or /usr/sbin... 

likely in the second listing...

after that create a symlink onto your desktop! :D
[B]
ln -s /program-location /home/<user>/Desktop/sensors-applet[/B]

---

### Post by nanotube on 2006-07-04
[QUOTE=MAXDDARK]I've installed this package - but I do not see it...were is it ? (I've checked applications and system and couldn't find it).[/QUOTE]
ah, heh, well this is the "tricky" part. jsut right click anywhere on your panel, select "add to panel" and find the "hardware sensors monitor" applet in the list and add it. :)

---

### Post by MaximB on 2006-07-04
[QUOTE=nanotube]ah, heh, well this is the "tricky" part. jsut right click anywhere on your panel, select "add to panel" and find the "hardware sensors monitor" applet in the list and add it. :)[/QUOTE]

I've found it - but it says "no sensors found"
what shell I do ?

---

### Post by nanotube on 2006-07-04
[QUOTE=MAXDDARK]I've found it - but it says "no sensors found"
what shell I do ?[/QUOTE]
did you right click on it, and select preferences, and then see a list of sensors? you have to manually select them from preferences of the applet.

also, what's your computer model? diff comps use diff sensors ...

also, you might have to reboot...

---

### Post by MaximB on 2006-07-04
when I click on preferances - it just all gray with nothing to select
yes I've restarted the PC
I have p4 1500MHZ RAM1GB

---

### Post by scxtt on 2006-07-04
you'll have to run "sensors-detect" to build the config file, then you might need to load the module (sensors-detect should let you know which one) ... so start out by typing **sensors-detect** into a terminal window ... this will allow you to add items to the gnome panel ... you'll know it's working when you can type **sensors** into a terminal and get something like:
```
:> sensors -f
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.42 V  (min =  +1.94 V, max =  +1.94 V)       ALARM
+12V:     +11.80 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.22 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +5.01 V  (min =  +4.75 V, max =  +5.25 V)
-12V:      +6.06 V  (min = -10.80 V, max = -13.18 V)       ALARM
V5SB:      +5.03 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +1.31 V  (min =  +2.40 V, max =  +3.60 V)       ALARM
fan1:        0 RPM  (min =   -1 RPM, div = 128)              ALARM
CPU Fan:  3096 RPM  (min =   -1 RPM, div = 4)              ALARM
fan3:     2700 RPM  (min = 84375 RPM, div = 4)              ALARM
M/B Temp:   +104°F  (high =   +45°F, hyst =   +32°F)   sensor = thermistor   ALARM
CPU Temp: +116.6°F  (high =  +176°F, hyst =  +167°F)   sensor = thermistor
temp3:     +29.3°F  (high =  +176°F, hyst =  +167°F)   sensor = thermistor
vid:      +0.275 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled
```

---

### Post by MaximB on 2006-07-05
it says that :
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.

what/how should I edit in mkdev.sh ?

---

### Post by confused57 on 2006-07-05
[QUOTE=MAXDDARK]I've found it - but it says "no sensors found"
what shell I do ?[/QUOTE]

You might need to configure lm-sensors using the link I gave you in an earlier reply...worked for me.

---

### Post by Anduu on 2006-07-05
[QUOTE=confused57]You might need to configure lm-sensors using the 2nd link I gave you in an earlier reply...worked for me.[/QUOTE]

Yep... lmsensors must be installed and properly configured for the sensors applet to work.

---

