---
title: "Newbie Question about heat and fans"
date: 2008-11-16
forum: Apple Hardware Users
---

### Post by RobSoko315 on 2008-11-16
Hi

I'm brand new to Ubuntu and Linux and therefore don't know much.  I'm using kernal 2.6

I have a Macbook Pro 3.1 (Santa Rosa) and it runs hot under Ubuntu.

The fans don't kick in (above 2000rpm) until the Cores hit 80 Degrees C.  This seems high, as Mac OS X puts the fans at 6000rpm when it hits this temperature.

How can I change the settings to do just that?

I've tried the command:

sudo echo > 3500 /sys/devices/platform/applesmc.768/fan1_min:

but get that I need permissions to do this.

I'm confused


Thanks for the help,

Rob.

---

### Post by gladioolers on 2008-11-16
I also need to know about this question's answer. But actually noone has answered it. I'll wait the answer. thanks.

---

### Post by _mario_ on 2008-11-16
> **RobSoko315 said:**
> 
The fans don't kick in (above 2000rpm) until the Cores hit 80 Degrees C.  This seems high, as Mac OS X puts the fans at 6000rpm when it hits this temperature.

How can I change the settings to do just that?

I've tried the command:

sudo echo > 3500 /sys/devices/platform/applesmc.768/fan1_min:

but get that I need permissions to do this.

have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=981280"). the bottom line is: fan speed is controlled by the hardware. you can change the minimum, if you like more noise, but your command was wrong. use this one:
```
echo 3500 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
```

however do not set the minimum to less than 1000 RPM. or at least check carefully. on my machine (MacBookPro 4), the fans start really late causing unhealthy temperatures under high load.

as kosumi68 pointed out, also check that manual control is turned off, i.e., _manual files report 0. this should be the default.

ciao,
Mario

---

### Post by RobSoko315 on 2008-11-16
Okay, thanks.  That line worked:)

My temperatures seem to max out at 80C now

---

### Post by hyperboloid on 2008-11-16
I created two scripts to increase and decrease the minimum fan speed, in order to have more control over this. First I created the file "fans-up" with the following lines:
```

echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 4000 | sudo tee /sys/devices/platform/applesmc.768/fan2_min

```
and made a corresponding file "fans-down" with:
```

echo 2000 | sudo tee /sys/devices/platform/applesmc.768/fan1_min
echo 2000 | sudo tee /sys/devices/platform/applesmc.768/fan2_min

```
to restore things to the original settings. Then I made both files executable by:
```

chmod +x fans-up
chmod +x fans-down

```
One can now run "./fans-up" to increase (minimum) fan speed and ./fans-down" to decrease it. 

As an added step, to make things nicer, one can create a hidden folder .bin in one's home directory with "mkdir .bin" and then move the scripts there. Then open up your .bashrc file with an editor and add the lines 
```

PATH=$PATH:$HOME/.bin
export PATH

```
at the end of the file. This includes your new folder ~/.bin in the search path, so that you can now execute your scripts from the command line no matter what folder you happen to be in. 

Hope it helps.

---

