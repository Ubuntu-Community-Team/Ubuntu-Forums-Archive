---
title: "some things turned off at boot"
date: 2009-11-04
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2009-11-04
Can someone help me to turn bluetooth of at boot/login ? I don't want to have bluetooth on while running Ubuntu. Another thing is how to have the power settings to "powersave" at boot/login all the time. It now always goes to on demand. I have laptop mode enabled and I have the following code in /etc/laptop-mode/conf.d/cpufreq.conf

```
CONTROL_CPU_FREQUENCY=1
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersafe
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=ondemand
NOLM_AC_CPU_IGNORE_NICE_LOAD=0
```

---

### Post by Nikos.Alexandris on 2009-11-04
> **linuxopjemac said:**
> Can someone help me to turn bluetooth of at boot/login ? I don't want to have bluetooth on while running Ubuntu. Another thing is how to have the power settings to "powersave" at boot/login all the time. It now always goes to on demand. I have laptop mode enabled and I have the following code in /etc/laptop-mode/conf.d/cpufreq.conf

```
CONTROL_CPU_FREQUENCY=1
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersafe
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=ondemand
NOLM_AC_CPU_IGNORE_NICE_LOAD=0
```

I want the same thing. How can we do it?

---

### Post by linuxopjemac on 2009-11-06
bump

---

### Post by linuxopjemac on 2009-11-06
To set it automatically for Intel Duo Core to preferred setting on startup, these lines should be added in /etc/rc.local


```
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

done

exit 0
```

---

### Post by linuxopjemac on 2009-11-06
to turn off bluetooth I simply made the bluetooth script in /etc/init.d not executable anymore

---

### Post by Nikos.Alexandris on 2009-11-08
> **linuxopjemac said:**
> to turn off bluetooth I simply made the bluetooth script in /etc/init.d not executable anymore

And what if you want to turn it on? Is the icon still there? Can you still use it?

---

### Post by linuxopjemac on 2009-11-08
the icon is there, it says bluetooth is disabled but I can still turn it off and on, so I don't really know what's going on there....

---

### Post by _mario_ on 2009-11-09
to turn off bluetooth or wifi, you might want to use the 'rfkill' command:
```

sudo rfkill block bluetooth

```

(or put this line without 'sudo' to /etc/rc.local if you like.)

---

### Post by aquavitae on 2009-11-09
I'm not in ubuntu at the moment, but I seem to remember that there is an option under the system menu.  I think that the menu item is called services and is under administration.  It has a list of startup services (including bluetooth) which you can enable or disable with a tick box.

---

### Post by linuxopjemac on 2009-11-09
there s only the bluetooth applet, probably not bluetooth itself

---

### Post by linuxopjemac on 2009-11-09
@ _mario_ thank you very much for that tip, I added your line in /etc/rc.local and now I have powersave at boot and bluetooth turned off:
```

echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
rfkill block bluetooth
```

---

### Post by ^_Pepe_^ on 2009-11-10
Thank you for the tip. 

It worked like a charm to deactivate BT at startup. Only a consideration. rfkill only work in 'karmic' kernels 2.6.31.

I've tried to do it in a 9.04 installation, installing git as mentioned here [http://www.linuxforums.org/forum/wireless-internet/154523-rfkill-query-tool.html](http://www.linuxforums.org/forum/wireless-internet/154523-rfkill-query-tool.html), but it doesn't work to me.

Thanks again!
^_Pepe_^

---

### Post by ^_Pepe_^ on 2012-11-02
For the record.

If anybody has a 3G internal modem, can disable it with

```
sudo rfkill block wwan
```

I have a new Thinkpad X201, and following powertop instructions is 0.8W less.

Regards

---

