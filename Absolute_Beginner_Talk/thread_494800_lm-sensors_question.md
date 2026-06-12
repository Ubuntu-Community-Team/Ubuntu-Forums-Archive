---
title: "lm-sensors question"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by killphil on 2007-07-07
Ubuntu newbie.  Having trouble getting lm-sensors to work.  I have tried this using methods from this forum, ubuntu guide, and softpedia.  With no luck.  I run Intel Desktop Utilities in Vista and I get temps and fan speed.  System specs:
Gateway GM5424 - Core 2 duo e6400 2.13GHz, Intel D965 MB, Nvidia GeForce 7300LE, 2GB RAM, Hitachi 400GB HDD

sudo sensors-detect results

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-i801
# Chip drivers
# no driver for Smart Battery Charger yet
# Warning: the required module smartbatt is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
smartbatt
eeprom
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)y
mike@Deathstarubuntu:~$ sudo /etc/init.d/module-init-tools
Password:
 * Loading kernel modules... 
 * Loading manual drivers... 


I can't find /etc/modules  or /etc/modprobe.d/local  to add any lines.  I have no clue what I'm doing and I need help.

---

### Post by forestpixie on 2007-07-07
"Do you want to add these lines to /etc/modules automatically? (yes/NO)[COLOR="Red"]y[/COLOR]"

It should have done it for you!

have you tried running sensors in Terminal?

---

### Post by killphil on 2007-07-07
Yes, here's what I got.

mike@Deathstarubuntu:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

---

### Post by mytwobears on 2007-07-07
Hi, I had the same exact problem with the same, exact results.  I answered yes to adding the script automatically but nothing happened and I don't have any of those two folders either.  Now when I try to run sensors-detect again it tells me it can't do it or it gets to the Super IO detection and then tells me I don't have the i2c kernel thing and so it can't do it.  I am pretty sure the i2c kernel files or whatever is there because I've seen the folder, but it won't detect it.  Also, when I try to initiate lm-sensors from the terminal, it won't do it.  So I just gave up.

Maybe someone can help us solve this :(.

---

### Post by Malta paul on 2007-07-07
Hi, 
I got 'LM Sensors' to work using the Terminal  command < sudo sensors-detect> and then followed the instructions.
 < sensors -f > shows the detected sensors found. I then went to  < system < preferences <Control Center >  and dragged the Icon to lower panel 'bar' . Right clicked preferences, <sensors> and ticked the box for the sensors I wanted. Which are CPU, Motherboard, HD temps, and cpu fan rpm.
You can also high-light the sensor you have ticked an set the temperature range, using properties
Hope this may help :D

---

### Post by killphil on 2007-07-07
still no luck

mike@Deathstarubuntu:~$ sensors -f
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

---

### Post by mytwobears on 2007-07-07
This is the output I receive:

cgp@Ubuntumobilecp:~$ sensors -f
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

---

### Post by Hork on 2008-02-17
Eh, I hate bumping an old topic but I'm having the same issue

---

### Post by gandaran on 2008-02-17
after running the sensors-detect thing, (which is easy just hit yes to every question) then you must install a program that users lm-sensors like » xsensors « or » gkrellm « reboot and start the program see if it works.

---

