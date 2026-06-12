---
title: "Fan control?"
date: 2007-06-13
forum: Apple Intel Users
---

### Post by Torajima on 2007-06-13
Okay, I've already done this bit (changing the value to 5000):

[SIZE="2"][I][COLOR="Blue"]    To set a minimum fan speed (helpful for making the MacBook run cooler) Add the following to /etc/rc.local: 

    echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed 

    Add the following to /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux (on a line by itself BEFORE the final "exit" statement) 
    echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed [/COLOR][/I][/SIZE]

But I don't think my fans are running any faster. Is there something else I have to install or edit first?

What exactly is "applesmc"?

---

### Post by pveith on 2007-06-13
Do a ```
sudo cat /sys/devices/platform/applesmc/fan0_actual_speed  
``` to get the actual speed. 

And to get max-Speed possible ```
sudo cat /sys/devices/platform/applesmc/fan0_maximum_speed
```.

Hope that helps...

---

### Post by Torajima on 2007-06-13
Thanks, that did help. Apparently I saved the wrong value in one of those files...

---

### Post by pveith on 2007-06-14
Keep in mind that these are not files in the normal sense. They represent the state in some memory registers and changes will be lost, as soon as you reboot. For a permanent change of behaviour you have to add the command [ echo 3000 > /sys/devices/platform/applesmc/fan0_minimum_speed] to the bootup script.

---

### Post by daller on 2007-06-19
How do I do this on a PC? (not mac...)

---

### Post by pveith on 2007-06-20
This is very hardware dependant. For my ASUS-Mainboard Based Desktop i had to do a lot of ml-sensors (sensors-detect) magic and load some module to get cpu-core-temp and fan-speeds. I never got around to be able to change them via the sys-filesystem.

So it might be a good idea to look into the lm-sensors package to get a gerenal idea.

---

