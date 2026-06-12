---
title: "MBP rev.3 temperature and fan control"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by zhark1 on 2008-05-26
Hello!

I've been experiment to get my MBP rev3 running as cool and silently as possible.

I've managed to get it down to 13,3 watts (measured with powertop, with brightness at minimum without beeing off) by unloading the iSight driver uvcvideo (/etc/modprobe.d/blacklist), enabling power management on wireless ("iwconfig wlan0 power on" in /etc/rc.local) and enabling laptop-mode (/etc/default/acpi-support). I also tried disabling the bluetooth module, but it only seems to use about 0,1W. 

To make it run more silently I set the fan1_min and fan2_min to 1500 in /sys/devices/platform/applesmc.768/.

I've experimented a bit by loading up glxgears while running a stress test with two threds to get both the CPU and videocard to suddenly produce a lot of heat. A while after i start stresstesting, the fans start to crawl upwards in RPMs, and after a while they're going fast enough to bring the CPU/GPU temperatures down again. What worries me is that the CPU is already well above 80C before the fans even start accelerating, and that they accelerate so slowly. I would really like for them to start accelerating earlier, maybe at about 60C. The temperature threshold seems to be controlled by hardware (maybe in EFI?). Is there any way to set this temperature threshold, maybe through the applesmc interface?

---

### Post by cyberdork33 on 2008-05-26
I don't think so. You can use coretemp to monitor the temperature of the CPU.

---

### Post by zhark1 on 2008-05-26
Ok. Yeah I forgot to mention, I'm using the sensors program from the package lm_sensors which reads information about fan speeds and temperatures from the applesmc and coretemp modules.

---

