---
title: "fan speed works on MacPro (I think...)"
date: 2008-02-01
forum: Apple Intel Users
---

### Post by mert on 2008-02-01
First, don't mistake me for someone who knows what they're doing, but I think fan speed control is working on the MacPro with the latest kernel.  I followed the directions here:
[http://ubuntuforums.org/showthread.php?t=442941](http://ubuntuforums.org/showthread.php?t=442941)
and here:
[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)
I used the .config from the macprolinux blog for kernel 2.6.23, but I installed 2.6.24, the latest on the linux kernel site.  I left everything as it is in the config and in the patches.  I am monitoring the fan speed and cpu temps with  the 'sensors' command, which reports:
CPU_MEM :  551 RPM (safe =    0 RPM, min =  500 RPM, max = 2900 RPM)
IO :       499 RPM (safe =    0 RPM, min =  500 RPM, max = 2900 RPM)

But these numbers fluctuate slightly every time I check it.  CPU temps are around the 50-60C range when the machine is idle and around 75-90C when the machine is under full cpu load.  the highest I have yet to see the CPU temp is 91C.  Is this similar to what other MacPro users are getting?
cheers

---

### Post by aztechclan on 2008-02-13
I am curious about this as well.  I have a 3rd gen macbookpro running Gusty.  I used the bash script from the ubuntu wiki santaRosa guide to control my fans (tempmon.sh).  I'm running the stock kernel with no mods besides installing MadWifi.  

Using this script I haven't seen the temp rise above low 70s.  Usually it's hovering in the high 50s range while surfing etc, and under load it jumps up rapidly but then the fans kick in full speed when it gets into the high 60s, low 70s.

90 sounds a bit high, I also setup some buttons to manually take over by doing:

#!/bin/bash
/etc/init.d/tempmon.sh stop
echo 6000 > /sys/devices/platform/applesmc.768/fan2_min
echo 6000 > /sys/devices/platform/applesmc.768/fan1_min

Others want to post their temperatures?  I know I'm watching mine very close with the sensors applet.

---

