---
title: "CPU Fan Speed &amp; Temp sensors for Linux?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Christopher on 2007-08-13
Is thier anything I can install that will show my CPU fan speed & temp on my desktop? Thank you in advance. :)

---

### Post by Steveway on 2007-08-13
$acpi -t
That should show the output of all temperature-sensors.

---

### Post by Christopher on 2007-08-13
Very nice, thank you. Any widget type thing?

---

### Post by Steveway on 2007-08-13
Sure. Try Conky. You can install it with Synaptic.

---

### Post by Christopher on 2007-08-13
Cool, thanks :)

---

### Post by ramjet_1953 on 2007-08-13
If you want a taskbar setup do the following:

[COLOR="Red"]sudo apt-get install hddtemp[/COLOR]

When it installs, it will ask you if you want the daemon to run at startup and also mentions the port to monitor, just click yes.

[COLOR="Red"]sudo apt-get install sensors-applet[/COLOR]

You now right click on either the top, or bottom taskbar and click on [COLOR="Blue"]Add to Panel[/COLOR].

Select [COLOR="Blue"]Hardware Sensors Monitor[/COLOR] and click [COLOR="Blue"]Add[/COLOR].

The icon will now appear in your taskbar.

Right click on the icon and choose [COLOR="Blue"]Preferences[/COLOR] to select the items you want to monitor and it will create a thermometer for each chosen item, including HDD temperature.

Don't forget to put a tick next to the items you want to monitor.

Regards,
Roger 8)

---

### Post by GregMcn on 2007-08-13
Excellent.Linux continues to amaze the limitless things you can do.

---

### Post by Arwen on 2007-09-01
Hello! I installed the stuff ramjet_1953 said but I can see only hard disk temp,there was no option for the cpu.When I typed acpi -t , I got "No support for device type: thermal".
Does anyone know what's wrong?
And what do I do when I simple type "acpi"?
Thanx for any help!

---

### Post by ubuntukerala1980 on 2007-09-01
gkrellm:lolflag:

---

### Post by bogolisk on 2007-09-01
> **Arwen said:**
> Hello! I installed the stuff ramjet_1953 said but I can see only hard disk temp,there was no option for the cpu.When I typed acpi -t , I got "No support for device type: thermal".
Does anyone know what's wrong?
And what do I do when I simple type "acpi"?
Thanx for any help!

install lm-sensors

```

sudo aptitude install sensors-applet lm-sensors hddtemp

```

add the Sensors Applet into a panel then configure it and select what you want to display.
[img]http://img103.mytextgraphics.com/photolava/2007/07/13/sensors-474w76iuf.png[/img]

---

### Post by louieb on 2007-09-01
The sensors you get depend on the sensors  on the machine. Like kiran.bhaskaran.nair I use  **gkrellm** for example my IBM T30 gives me CPU, Hard drive, and battery temperature but not fan speed.   On one desktop all I get is thermal temp.

---

### Post by Arwen on 2007-09-01
I installed lm sensors but I still can't see cpu fan speed and temp in the sensors applet preferences.I can't see my cpu at all..System monitor shows it as dual core(it's p4 @ 3GHz that supports hyper threading)

---

### Post by bogolisk on 2007-09-01
> **Arwen said:**
> I installed lm sensors but I still can't see cpu fan speed and temp in the sensors applet preferences.I can't see my cpu at all..System monitor shows it as dual core(it's p4 @ 3GHz that supports hyper threading)

This might crash your machine but if you really want to try:

```

sudo sensors-detect

```

The script will try to detect what sensor chip is on you motherboard so you'd know which sensor module to load into the kernel.

---

### Post by mastergunner on 2007-09-01
Will this work for laptops as well or is there something better for laptops?

---

### Post by bogolisk on 2007-09-01
> **mastergunner said:**
> Will this work for laptops as well or is there something better for laptops?

It really depends on the motherboad and the way it provides this information to software.

---

### Post by mastergunner on 2007-09-01
I just used the code written below and I have nothing. It all installed but how do I run it. Nothing has come up in the taskbar or in any drop down bar. A little help please.



> **bogolisk said:**
> install lm-sensors

```

sudo aptitude install sensors-applet lm-sensors hddtemp

```

add the Sensors Applet into a panel then configure it and select what you want to display.
[img]http://img103.mytextgraphics.com/photolava/2007/07/13/sensors-474w76iuf.png[/img]

---

### Post by nonewmsgs on 2007-09-01
excellant thread.  definitely the kind i bookmark to check back on.

---

### Post by m9ke on 2007-09-01
mastergunner check out ramjet_1953's comment in this thread:

[http://ubuntuforums.org/showthread.php?t=321948&highlight=add+applet](http://ubuntuforums.org/showthread.php?t=321948&highlight=add+applet)

I got stuck here too, and this seems to be working for me.

m9ke

---

### Post by bogolisk on 2007-09-01
> **mastergunner said:**
> I just used the code written below and I have nothing. It all installed but how do I run it. Nothing has come up in the taskbar or in any drop down bar. A little help please.

AFAIK, in labtops usually provides info/control of fan/temp via ACPI while desktop usually uses the SMBus. The sensors-applet can use either. I don't use ACPI so I have no idea what need to be done. For the lm-sensors to work with your motherboard SMBus, you'll have figure out the chip (usually a variant of winbond hw monitor IC) and load the correct module. My motherboard has a 
w83627eh chip and module to load was w83627ehf. The best way to figure out the hw monitor chip is to read the motherboard manual. Other than than try the code below to detect the chip
```

sudo sensors-detect

```
add the detected module into /etc/modules

---

### Post by lmlypfan on 2007-09-01
ramjet,

I installed the application, but my cpu temp never changes, even under heavy load. WTF
all other sensors look good, but cpu stays at 40 degrees?

help

---

### Post by Arwen on 2007-09-02
I did sudo sensors-detect and after a sequence of questions in which I answered "yes" it changed my /etc/modules.Nothing has crashed till now..

---

### Post by bogolisk on 2007-09-02
> **Arwen said:**
> I did sudo sensors-detect and after a sequence of questions in which I answered "yes" it changed my /etc/modules.Nothing has crashed till now..

Cool, just curious what did it add into your /etc/modules? And what you see running
```

sensors

```

---

### Post by PmDematagoda on 2007-09-02
I did sudo sensors-detect just now and got the choice of adding the following to etc/modules:

```
#----cut here----
# I2C adapter drivers
i2c-i801
# modprobe unknown adapter NVIDIA i2c adapter
# modprobe unknown adapter NVIDIA i2c adapter
# modprobe unknown adapter NVIDIA i2c adapter
# Chip drivers
lm85
eeprom
#----cut here----

```

I think this may crash the system due to the 3 # modprobe unknown adapter NVIDIA i2c adapter's.
Does anyone have an alternative?

---

### Post by Arwen on 2007-09-02
It added :
fuse
lp

# Generated by sensors-detect on Sun Sep  2 14:18:49 2007
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-viapro
# Chip drivers
eeprom
w83627hf

----
when I do "sensors" I get:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

---

### Post by bogolisk on 2007-09-02
> **Arwen said:**
> It added :
fuse
lp

# Generated by sensors-detect on Sun Sep  2 14:18:49 2007
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-viapro
# Chip drivers
eeprom
w83627hf

----
when I do "sensors" I get:
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

/etc/modules is only used at boot time. For your current session, try
```

sudo modprobe w83627hf

```

---

### Post by bogolisk on 2007-09-02
> **PmDematagoda said:**
> I did sudo sensors-detect just now and got the choice of adding the following to etc/modules:

```
#----cut here----
# I2C adapter drivers
i2c-i801
# modprobe unknown adapter NVIDIA i2c adapter
# modprobe unknown adapter NVIDIA i2c adapter
# modprobe unknown adapter NVIDIA i2c adapter
# Chip drivers
lm85
eeprom
#----cut here----

```

I think this may crash the system due to the 3 # modprobe unknown adapter NVIDIA i2c adapter's.
Does anyone have an alternative?

Do you have a nforceX motherboard? try
```

sudo modprobe lm85
sensors

```

Or try
```

sudo modprobe i2c_nforce2
sudo sensors

```

---

### Post by Arwen on 2007-09-02
My m/b is ASRock 775VM800 and sudo sensors gave me:

Adapter: ISA adapter
VCore:     +1.30 V  (min =  +0.16 V, max =  +0.26 V)       ALARM  
+3.3V:     +3.31 V  (min =  +2.05 V, max =  +0.26 V)       ALARM  
+5V:       +5.13 V  (min =  +0.11 V, max =  +1.32 V)       ALARM  
+12V:     +11.55 V  (min =  +0.49 V, max =  +0.24 V)       ALARM  
-12V:      +1.13 V  (min = -14.75 V, max = -14.91 V)       ALARM  
-5V:       +2.34 V  (min =  -6.10 V, max =  -7.21 V)       ALARM  
V5SB:      +5.51 V  (min =  +5.16 V, max =  +0.86 V)       ALARM  
VBat:      +0.61 V  (min =  +2.10 V, max =  +0.03 V)       ALARM  
fan1:        0 RPM  (min =   -1 RPM, div = 8)              ALARM  
fan2:     3308 RPM  (min = 1171 RPM, div = 8)                     
temp1:       +42°C  (high =    +0°C, hyst =    +0°C)   sensor = thermistor   ALARM   
temp2:     +47.5°C  (high =   +80°C, hyst =   +75°C)   sensor = diode           
alarms:   
beep_enable:
          Sound alarm enabled


so I think everything is ok.
Thanx a lot guys!! :-)

---

### Post by PmDematagoda on 2007-09-02
I have an Intel D915GAV motherboard with LGA775 processor socket.

P.S. Anyone who uses a motherboard and processor similar to mine would agree that things get really hot there, so I would appreciate any help to solve this problem.

---

### Post by mramsey on 2007-09-05
> **bogolisk said:**
> install lm-sensors

```

sudo aptitude install sensors-applet lm-sensors hddtemp

```

add the Sensors Applet into a panel then configure it and select what you want to display.
[img]http://img103.mytextgraphics.com/photolava/2007/07/13/sensors-474w76iuf.png[/img]

The only sensor I get to show up is the HDD. :confused: Can you add HDD's that are on a NAS box?

---

### Post by svdb on 2007-10-07
> **GregMcn said:**
> Excellent.Linux continues to amaze the limitless things you can do.

Hmmm
To dynamically change VCore, stepping, cpu clock... without having to type a single cmd line:
[http://crystalmark.info/software/CrystalCPUID/index-e.html](http://crystalmark.info/software/CrystalCPUID/index-e.html)

To read all of your volts, speeds and temps... without having to type a single cmd line:
[http://www.almico.com/sfscreenshots.php](http://www.almico.com/sfscreenshots.php)

...and display all that info on a nice LCD panel... without having to type a single cmd line:
[http://www.vlsys.co.kr/](http://www.vlsys.co.kr/)

Ooops! wrong thread I guess, all this was for Windows... \\:D/

---

### Post by Jose Catre-Vandis on 2007-10-09
lol @ svdb

Now my Edubuntu 6.06 returns:
```
no i2c devices found
```
when I run
```
sudo sensors-detect
```
not had this before on other machines?

---

