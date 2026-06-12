---
title: "N55 Tempurature Question"
date: 2012-09-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by monk0nuggets on 2012-09-06
So, I've been running Ubuntu 12.04 since a couple of months before the official release.  Everything seemed as right as it should without any official NVIDIA drivers.  Recently I've been getting an error message upon booting every time, and it seems to be running quite warm, around 59-60 Celsius while running basic programs like Firefox or Libre Writer according to PSensor.  Is this too hot?  It seems like it would be considering what I'm running.

---

### Post by Petro Dawg on 2012-09-06
I was running much hotter than that ~70°c, then I switched to unity2d and installed jupiter.  Now I typically run less than 50°c during normal use, I still get up to around 70 when playing nexuiz (used to be over 90).  I would suggest logging into 2d mode and seeing if that makes a difference for you.

---

### Post by monk0nuggets on 2012-09-06
Jupiter eh?  I'll have to look into that.

---

### Post by jeanfi on 2012-09-06
> **monk0nuggets said:**
> Recently I've been getting an error message upon booting every time, and it seems to be running quite warm, around 59-60 Celsius while running basic programs like Firefox or Libre Writer according to PSensor.  Is this too hot?  It seems like it would be considering what I'm running.

By default, Psensor is raising an alert when the temperature is greater than 60C but that's only a default and does not take care of the sensor type. 60C is not hot for most of the CPUs and GPUs but it can be hot for a HDD. You should take a look at your the specification of your HW to determine the 'too hot' temperature and set it in the Psensor configuration of the sensors.

---

### Post by illegal on 2012-09-10
how do you monitor the temperature on ubuntu? i am on an ausuX54C laptop with ubuntu 12.04

any app available?

---

### Post by jeanfi on 2012-09-11
> **illegal said:**
> how do you monitor the temperature on ubuntu? i am on an ausuX54C laptop with ubuntu 12.04

any app available?

There are multiple UI applications for monitoring temperature, xsensors and psensor are in the standard ubuntu repository, so you can install them easily from the software center.

There is also indicator-sensors from Alex Murray that you can install from a PPA, see [https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors).

Note, that these UI applications are requiring to first install lm-sensors and configure it correctly:
> sudo apt-get install lm-sensorsThen, starts the detection of your hardware sensors:
 > sudo sensors-detectFollow the instructions carefully, and finally verify that it works:
 > sensors It should display something like:> 
 coretemp-isa-0000 
Adapter: ISA adapter 
Core 0:      +46.0C  (high = +76.0C, crit = +100.0C)  
coretemp-isa-0001 
Adapter: ISA adapter 
Core 1:      +44.0C  (high = +76.0C, crit = +100.0C)  ...
If you follow these steps all UI applications should work correctly, at least if your HW is supported by lm-sensors.

---

### Post by illegal on 2012-10-04
> **jeanfi said:**
> There are multiple UI applications for monitoring temperature, xsensors and psensor are in the standard ubuntu repository, so you can install them easily from the software center.

There is also indicator-sensors from Alex Murray that you can install from a PPA, see [https://launchpad.net/~alexmurray/+archive/indicator-sensors](https://launchpad.net/~alexmurray/+archive/indicator-sensors).

Note, that these UI applications are requiring to first install lm-sensors and configure it correctly:
Then, starts the detection of your hardware sensors:
 Follow the instructions carefully, and finally verify that it works:
 It should display something like:
If you follow these steps all UI applications should work correctly, at least if your HW is supported by lm-sensors.

Thanks man!
I did exactly as per your instruction, and got the following output after giving the 'sensors' command.
> ~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +50.0°C  (crit = +88.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:        +50.0°C  

Is the system temperature OK, normal or abnormal?

---

