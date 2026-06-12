---
title: "[SOLVED] CPU temperature"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Johnny3 on 2007-09-12
I have a AMD Athlon 64x2 4600+(65) windson with a ASUS M2N-E  BISOE 08.02 and ASUS video card EN7600GS. 
I have been typing in acpi -t and it says the CPU is 40.0c no mater what I am doing it is alway 40.0c don't think it is working to get CPU temperature. I did not install anything to run acpi -t. Should I ?
I found how to install Install lm-sensors here [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) 
all I did was sudo apt-get install lm-sensors and then sudo sensors-detect. I didn't know how to 

2. Run the mkdev.sh script in the lm-sensors source. It is extacted below:

a. Copy the script file below to a text editor and save it to a file named mkdev.sh.

#!/bin/bash

# Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1]
done
#end of file

b. Make the file executable:

chmod 755 mkdev.sh

c. Run mkdev.sh from the current directory

sudo ./mkdev.sh


When I type sensors I get

johnny@johnny-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +25°C
Core1 Temp:
             +28°C

it8716-isa-0290
Adapter: ISA adapter
VCore:     +1.14 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:      +3.22 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:       +4.81 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +11.39 V  (min =  +0.00 V, max = +16.32 V)   
in5:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:       +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:      +4.81 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +2.98 V
fan1:     5192 RPM  (min =    0 RPM)                   
fan2:        0 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +29°C  (low  =    -1°C, high =  +127°C)   sensor = diode   
temp2:       +35°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
temp3:        -3°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
vid:      +1.250 V

Since I didn't do this  Run the mkdev.sh script in the lm-sensors source
I get temp 1 which is the MB and temp 2 which is the CPU is this right? Are the Core 0 and Core 1 just each side of the CPU?
I and new at this wish I could have done step 2
I am using Ubuntu 7.04 32bit 
Thanks Johnny3
Gainesville Fl

---

### Post by harlan on 2007-09-12
I think you did something wrong, because the information about lm-sensors in the link you posted is right. Visit [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sen") & try to follow its recommendation.
(I don't understand well what you did, but I think you forget adding the modules)

---

### Post by cubeist on 2007-09-12
whoa!  Thats way too complicated... I use a simple app called computer temperature monitor.
[http://computertemp.berlios.de/]("http://computertemp.berlios.de/")

It just sits in my panel and I have found it to be fairly accurate...

---

### Post by Johnny3 on 2007-09-13
Thanks I just installed it. [http://computertemp.berlios.de/help.php](http://computertemp.berlios.de/help.php)  Did known how to do 
How to compile and install
First of all, you need to install these dependencies:
- python
- pygtk (>= 2.4)
- gtk development libraires
- gconf2
- python-gnome
- python-gnome-extras (python-gnome-desktop if you're using Gnome >= 2.14)
- common build tools (autotools and libxml-parser-perl)

Ok, so we're done with dependencies. Now execute this commands:

$ tar xzvf computertemp-0.9.0-tar.gz
$ cd computertemp-0.9.0/
$ ./configure --prefix /usr (this is for most distros)
$ make
$ sudo make install (or su -c "make install")

I see
9191-0290 (1) 31c
9191-0290 (2) 36c
I thinks 1 is MB and 2 is CPU what do you think?
Thanks Johnny
Gainesville Fl

---

### Post by philinux on 2007-09-13
I use mbmon from the repo. Simple terminal app.

---

### Post by Johnny3 on 2007-09-13
I am new to all this. I found mbomon and xmbomon in Synaptic Package manager. Which one would be better for some one That doesn't know much. Do I need to type something in the Terminal after I install one of them in Synaptic Package manager. 
Thanks Johnny3
Gainesville Fl

---

### Post by philinux on 2007-09-13
mbmon works by going to the terminal and typing sudo mbmon. you can easily set up a launcher on the desk top or edit menus and place a launcher in there.

In synaptic just search for **mbmon**

---

### Post by rfurman24 on 2007-09-13
I am a little confused about all the work to get lm-sensors working. I just intalled via synaptic then ran sensors-detect in a terminal and answered all the questions then rebooted and all works as it should. I did not doing any of that file editing. I am not sure but I think that is for and older version of Ubuntu.

---

### Post by cubeist on 2007-09-13
> **Johnny3 said:**
> 
9191-0290 (1) 31c
9191-0290 (2) 36c
I thinks 1 is MB and 2 is CPU what do you think?
Thanks Johnny
Gainesville Fl

Those temperatures seem a bit low.  Either you have really decent cooling or you are viewing a hdd sensor.  My dual-core athlon runs between 50 - 60 C.  If you right-click on the icon and select preferences there should be a list of the available sensors.  I find the ACPI sensor gives me the best temp reading.  When in doubt just monitor the sensor that constantly produces the highest temp because that is probably the CPU.

---

### Post by w4ett on 2007-09-13
The sure way to verify your CPU temps is to check it in the Motherboard Bios...there should be a Hardware Monitor section in your system settings......Verify that it is close (or the same) as what you are seeing in lm-sensors.

---

### Post by rfurman24 on 2007-09-13
I am pretty sure temp one is the motherboard and temp two is the cpu as it is on my system. Those temps should be about right at idle. My system runs a little warm(I'm working on that) and reports temps slightly higher.

---

### Post by w4ett on 2007-09-13
> **rfurman24 said:**
> I am pretty sure temp one is the motherboard and temp two is the cpu as it is on my system. Those temps should be about right at idle. My system runs a little warm(I'm working on that) and reports temps slightly higher.

Thats what it is on mine Temp1 is Motherboard and Temp 2 is CPU (running an overclocked Athlon XP 2400 @ 2.6 Ghz.

---

### Post by rfurman24 on 2007-09-13
You marked this thread as solved. What did you do to solve it? Posting what you did to solve the problem might help others.

---

### Post by slick_nick on 2008-04-30
Easy way to get sensors working: *sudo apt-get install* both *lm-sensors* and *sensors-applet*. Run sudo sensors-detect.  Restart, right-click top bar, click Add to Panel, find Hardware Sensors Monitor. voila!

---

