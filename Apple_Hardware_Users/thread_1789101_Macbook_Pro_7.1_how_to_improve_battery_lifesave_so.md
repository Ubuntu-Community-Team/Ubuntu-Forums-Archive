---
title: "Macbook Pro 7.1 how to improve battery life/save some watts under Ubuntu 11.04 64bit?"
date: 2011-06-23
forum: Apple Hardware Users
---

### Post by vickoxy on 2011-06-23
Hi,
i read lot´s of threads how to extend battery life and save some watts here, but every generation of Macbooks Pro has specifical hardware. My MBP use  about 13-14 Watts with firefox, 90% Display, and powertop running behind (with Bluetooth and Wifi). But as soon as i work with more programs, it goes up to 20-25 watts. So, at the end, i have on MacBook Pro under 11.04 maybe 3-3,5 hours, under MacOS 5-6 hours. 
So, if anyone has some idea how to increase battery life, and know how to explain it to average user - welcome!

I activated on my MBP this program/script: [http://thinkpad-wiki.org/TLP_-_Stromspareinstellungen_f%C3%BCr_Ubuntu](http://thinkpad-wiki.org/TLP_-_Stromspareinstellungen_f%C3%BCr_Ubuntu)
This is script made for Thinkpads, but  on MBP, because before installation my battery life was even worst, and i had really lot of wakeups (now in idling i have 180-190 wakeups, still high number?).

---

### Post by handy on 2011-06-23
I think that Fuduntu is one of, if not the best distro around for saving power. If power management is a priority for you it may be worth having a look at Fuduntu. 

A new release came out inside of the last week as well.

Alternatively, you could look at installing Jupiter:

[http://www.jupiterapplet.org/index.html](http://www.jupiterapplet.org/index.html)

As it may give you the control you need.

---

### Post by vickoxy on 2011-06-23
Well, Jupiter doesn´t support Ubuntu, Fuduntu - not sure, i adjusted my MAcBook and Ubuntu and would like to make ubuntu more efficient, rather than installing new system.

---

### Post by marin123 on 2011-06-23
are you using compiz? if you need battery power you can disable the effects, because the gpu is a big drain.
also you can lower processor frequency. old gnome had an applet to do that, i dont know how in natty...

---

### Post by vickoxy on 2011-06-23
Yes i have compiz activated. Still wouldn´t have it disabled because then i can not use cairo-dock, ring switcher, etc.
So, there are no ways to deactivate some processes or to improve battery life without cutting some effects?

---

### Post by marin123 on 2011-06-23
> **vickoxy said:**
> Yes i have compiz activated. Still wouldn´t have it disabled because then i can not use cairo-dock, ring switcher, etc.
So, there are no ways to deactivate some processes or to improve battery life without cutting some effects?

you can run ccsm and disable animations. that should get rid of minimize, maximize, close animations. and you can disable desktop cube and keep desktop wall. i guess thats it for compiz power save.

---

### Post by vickoxy on 2011-06-23
Disabled animations and cube-don´t need it really. Thanks-we´ll see  if it brings something...
So, here is one output of my powertop. The most wakeups are caused by > 44,1% (267,2)   [eth1, nvidia] <interrupt>? Is there any way to decrease it? Another question: > 3,3% (  8,3)   USB Gerät  2-1 : Card Reader (Apple) is always on-any way to shut it down if i don´t use it?

---

### Post by vickoxy on 2011-06-24
Hi, after installing/deinstalling jupiter i have one problem. After restart my cpu governor is always on performance. Anyone knows how to set it back ondemand?
My gksudo gedit /etc/init.d/ondemand is:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
	;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

I made ```
sudo-update initramfs -u
```, but nothing-it stays always on performance (manually i can change it-untill next reboot)

Any help here?

---

