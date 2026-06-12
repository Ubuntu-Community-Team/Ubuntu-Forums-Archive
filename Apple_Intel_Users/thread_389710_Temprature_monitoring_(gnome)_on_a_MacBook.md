---
title: "Temprature monitoring (gnome) on a MacBook"
date: 2007-03-21
forum: Apple Intel Users
---

### Post by gmc on 2007-03-21
Hi Folks,

After a short struggle to get Ubuntu installed on my brand spanking new MacBook (13" White 2.0Ghz C2D). I'm wondering how I can monitor the CPU temprature? I have an Acer 5672 (CD) and use ComputerTemp to monitor the temprature but this program doesn't work on the MacBook? Do I have to play with the lmsensors package or is there another way?

Gord

---

### Post by david_edmundson on 2007-03-21
I don't believe it is working without a lot of fiddling at the moment. Patches have been made by "Mactel" though they haven't made it through to the main kernel yet.

Gentoo's wiki seems to know best so I'll c&p it.

Hardware Sensors 
The Intel 82801 (ICH) is the correct driver for the I2C bus, but I do not know what the drivers for any sensors are, if they exist. 
The CPUs temperature can be fetch by using this little C code: [http://svn.sourceforge.net/viewvc/mactel-linux/trunk/tools/temperature/](http://svn.sourceforge.net/viewvc/mactel-linux/trunk/tools/temperature/) 
The new lm_sensors package contains a "coretemp" driver and allows reading temperature. 
Non-official "applesmc" driver offers extended temperature info, fan control/info and motion sensor info. It also supports light sensors and keyboard backlights on the Macbook Pro. 
A kernel patchset for this can be found here. 
The disk temperature can be fetch using hddtemp.

---

### Post by gmc on 2007-03-22
Hi David,

Thanks for pointing me in that direction. Looks like that source hasn't been updated in a while, but at least its a start.

Gord

---

### Post by PictureThis on 2007-03-28
I'm running Kubuntu and I'm trying to figure out why I haven't heard my fan yet. The MacBook is definitely getting hotter than on OSX but I'd really like to backup that statement with temperature facts. Yesterday I logged out from Kubuntu when the MacBook ran really hot, especially near the bottom power jack area (running on battery power), rebooted to OSX and immediately the fan was put into motion.

Right now, all I have is this:
```
acpi -V
     Battery 1: discharging, 46%, 01:18:00 remaining
No support for device type: thermal
  AC Adapter 1: off-line

```

Not quite enough to do some serious probing.

---

### Post by gmc on 2007-03-28
Hi

> **PictureThis said:**
> I'm running Kubuntu and I'm trying to figure out why I haven't heard my fan yet. The MacBook is definitely getting hotter than on OSX but I'd really like to backup that statement with temperature facts. Yesterday I logged out from Kubuntu when the MacBook ran really hot, especially near the bottom power jack area (running on battery power), rebooted to OSX and immediately the fan was put into motion.

Right now, all I have is this:
```
acpi -V
     Battery 1: discharging, 46%, 01:18:00 remaining
No support for device type: thermal
  AC Adapter 1: off-line

```Not quite enough to do some serious probing.

This is a bit worry some! What does the following report?

```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```

Gord

---

### Post by PictureThis on 2007-03-28
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
ondemand

```

hovering over the battery indicator shows:
**CPU Frequency:** Dynamic

Processor 1: 1000 **MHz**
Processor 2: 1000 **MHz**

(Interesting terminology, I thought the MacBook Core 2 Duo was equipped with a single processor but with two cores)

---

### Post by gmc on 2007-03-28
> **PictureThis said:**
> ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
ondemand

```hovering over the battery indicator shows:
**CPU Frequency:** Dynamic

Processor 1: 1000 **MHz**
Processor 2: 1000 **MHz**

(Interesting terminology, I thought the MacBook Core 2 Duo was equipped with a single processor but with two cores)

Ouch! that's not good then. Ondemand means that the processor(s) will kick into high gear if the load on the cpu demands it. If the demand remains high for any length of time, your cpu's will heat up very quickly. If the fan is not kicking in, then it's possible to damage them.

In KDE, I'm not sure how to tell the system to put the processor in powersave mode, but here's how I do it.

In stall **sysfsutils **```
sudo apt-get install sysfsutils
``` then as root edit **/etc/sysfs.conf **and add the following lines ```
devices/system/cpu/cpu0/cpufreq/scaling_governor = powersave
devices/system/cpu/cpu1/cpufreq/scaling_governor = powersave
``` now, either reboot the system or issue the following command ```
sudo /etc/sysfsutils restart
```This will force the cpu's into powersave mode which means they will never kick into high speed mode. This is a stop-gap measure, until we can figure out why/how your fan is not kicking in.

Gord

---

### Post by PictureThis on 2007-03-28
Thanks gmc, I was able to put the scaling_governor parameter into powersave mode via Power Manager (click the battery/power indicator)

I checked via:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
powersave
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
powersave

```

This should do for now.

---

### Post by PictureThis on 2007-03-29
This is interesting: Right after I installed the [lm_sensors](http://www.lm-sensors.org/) package I rebooted and that was the **first time** the fan started spinning during a Kubuntu session, the fan kicked right in with splash screen showing. I gave it some time until the fan had quieted down. Then I put the processor to work by means of some [daily show videoplay](http://www.comedycentral.com/shows/the_daily_show/index.jhtml) and now my fan **does** work in a Kubuntu session. I don't feel the need to test it again by uninstalling the lm_sensors package, sorry. :neutral:  

As for reading CPU temperature by means of coretemp mentioned by david_edmundson:

I receive this message when executing:
```
sudo ./coretemp
Maybe you need to load the msr kernel module?
/dev/cpu/0/msr: No such file or directory
```

Any suggestions?

Edit: OK, Let's try modprobe msr? Yes...
```
sudo ./coretemp
CPU 0: 60 °C
CPU 1: 60 °C
```

Now we're getting somewhere..

---

### Post by teymour on 2007-04-30
To get sysfs working correctly, I had to insert the following lines into /etc/modules :
```

acpi_cpufreq
cpufreq_powersave

```

---

