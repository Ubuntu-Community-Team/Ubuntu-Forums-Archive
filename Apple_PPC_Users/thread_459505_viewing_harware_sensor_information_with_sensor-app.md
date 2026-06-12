---
title: "viewing harware sensor information with sensor-applet"
date: 2007-05-30
forum: Apple PPC Users
---

### Post by tr333 on 2007-05-30
I have installed sensor-applet for the gnome toolbar to view the hardware sensor information.  I also installed hddtemp and I can see that in the sensor-applet.  What else do I need to install to view other hardware sensors?  This is on a Powerbook 12'' G4 (1.5GHz).

---

### Post by dave-5B on 2007-06-01
this

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29)

---

### Post by stmiller on 2007-06-01
Type

sensors

in a terminal. What is the output? 
Most of these sensors in the kernel are not made for Mac hardware, unfortunately.

---

### Post by tr333 on 2007-06-02
> **stmiller said:**
> Type

sensors

in a terminal. What is the output? 
Most of these sensors in the kernel are not made for Mac hardware, unfortunately.

looks like i should install lm-sensors :)

how does ubuntu know what package to install when i type the command of something that isn't installed?

---

### Post by jorik on 2007-07-05
I have the opposite problem. I have configured lm-sensors (and fancontrol) and those values are perfectly showing on my panel, but I cannot see hddtemp in my Sensors Applet. The only Sensor group that is being detected is libsensors.

hddtemp is running as daemon, because
$ ps aux | grep hddtemp
gives:
root      5218  0.0  0.0   3916   676 ?        S    13:21   0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sda

Is there anything I'm missing here? I am running Feisty amd64.

---

### Post by tr333 on 2007-07-14
> **jorik said:**
> I have the opposite problem. I have configured lm-sensors (and fancontrol) and those values are perfectly showing on my panel, but I cannot see hddtemp in my Sensors Applet. The only Sensor group that is being detected is libsensors.

hddtemp is running as daemon, because
$ ps aux | grep hddtemp
gives:
root      5218  0.0  0.0   3916   676 ?        S    13:21   0:00 /usr/sbin/hddtemp -d -l 127.0.0.1 -p 7634 -s | /dev/sda

Is there anything I'm missing here? I am running Feisty amd64.

Is the hddtemp daemon running on the default port?  If you changed the port number when installing from apt-get, then the sensors applet won't be able to find it.

---

