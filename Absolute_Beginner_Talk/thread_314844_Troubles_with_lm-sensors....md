---
title: "Troubles with lm-sensors..."
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-08
Hi,

I just undervolted my CPU and I'd like to display the sensors information (voltage, temperature etc) in the "taskbar". I will use Gnome sensor applet to display the info but I first need to install lm-sensors. I followed this guide [http://www.linuxquestions.org/questions/showthread.php?t=473997](http://www.linuxquestions.org/questions/showthread.php?t=473997) but I have 2 issues:

1) on step 5 of the guide, when I do sudo modprobe i2c-sensor I get the following message:
FATAL: Module i2c_sensor not found.

All other sensors seem to exist.

2) At the end when I type "sensors" in the terminal I get the follwoing message:

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!



Any idea what I should do? I don't really understand what all this means.

Thanks


PS: I'm running Edgy with kernel 2.6.19 (patched with Linux-phc) on an MSI S260 notebook.

---

### Post by teaker1s on 2006-12-08
Don't quote me on this but it appears that the kernel module isn't loaded I believe it's 
'lm sensors'
 if you install
 "module-assistant" 
then 
"sudo module -assistant"
 you can graphically install and set kernel modules to load
from personal experience not all motherboards are fully compatible

---

### Post by pay on 2006-12-08
Try this```
sudo module-rebuild rebuild
```

---

### Post by pay on 2006-12-08
Also try ```
sudo su
echo "lm_sensor" >> /etc/modules.autoload.d/kernel-2.6 
modules-update
exit
```And make sure that your kernel is compilled with support for sensors.```
cd /usr/src/linux
sudo make menuconfig
``````
I2C support  --->
<M> I2C support
<M>   I2C device interface
      I2C Hardware Bus support  --->
      <M> Choose the appropriate module(s) for your hardware

```and```
Hardware Monitoring Support --->
<M> Hardware Monitoring support
<M> Choose the appropriate module(s) for your hardware
```and```
DEVICE Drivers --> hardware monitoring support --> <M> hardware monitoring support 
```and then try ```
rc-update add lm_sensors default
```I'm a Gentoo  user and I found this information on Gentoo sites so don't blame me if Ubuntu is different and it doesn't work.

---

### Post by kilou on 2006-12-08
Tried all this (most thing did not work on my Ubuntu) but still get the same error message :(

---

### Post by pay on 2006-12-08
This guide here [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) tells you weither your mainboard is supported or not. So when you had entered your kernel's config file, did you have all these options ticked off?```
Device Drivers ---> Hardware Monitoring Support --->
<M> Hardware Monitoring support
<M> Choose the appropriate module(s) for your hardware

```and```
Device Drivers ---> I2C support  --->
<M> I2C support
<M>   I2C device interface
      I2C Hardware Bus support  --->
      <M> Choose the appropriate module(s) for your hardware
```And it still didn't work?

---

### Post by kilou on 2006-12-09
I checked the parameters running make menuconfig and it seems I have everything checked. The only think unchecked under I2C hardware bus support is opencores I2C controllers. Should I enable this module?? By the way if I want to make such a change, can I just modify it in make menuconfig and then save the changes or do I need to recompile the kernel??

I read somewhere that lm-sensors shouldn't be used on laptop. I don't remember why but I think it was recommended to get sensor info through ACPI... I could see many threads where people have troubles with lm-sensors and get the exact same message as me but I couldn't find a fix. My goal is to get CPU and HDD temperatures (I need to install hddtemp I think), CPU frequency and voltage etc all in the same application. Is there alternatives to GKrellm for this?

---

