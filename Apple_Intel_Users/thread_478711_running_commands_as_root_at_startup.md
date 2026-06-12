---
title: "running commands as root at startup"
date: 2007-06-19
forum: Apple Intel Users
---

### Post by erkker on 2007-06-19
I found this code:

sudo sh -c "echo 5000 > /sys/devices/platform/applesmc/fan0_minimum_speed"

to increase my fan speed so that my MBP will not melt (or seem to )

Now is there a way to run this at startup automatically?  It needs root access so thats my main issue, though I dont know how to run a command at startup to begin with.

Sorry if overly noob.

-E

---

### Post by Rui Pais on 2007-06-19
Hi,
Check [this thread here]("http://ubuntuforums.org/showthread.php?p=2875632").

---

### Post by david_edmundson on 2007-06-19
Actually there is a better way to do that particular function. What you're doing is waiting till it all loads then changing the value via a script (which is a perfectly valid technique). A better solution is to just  to make it load the correct default. (this is done by root at load time so permissions aren't an issue)

Do this by adding a line to /etc/sysctl.conf
devices.platform.applesmc.fan0_minimum_speed=5000

check all is good by running
cat /sys/devices/platform/applesmc/fan0_minimum_speed after a reboot

Full manual on this is at the usual place (type "man sysctl.conf" in a terminal)

There's no way you'd be expected to know this as a LInux user, it's just something I learnt from asking a very similar question on a mailing list.

---

### Post by vh1 on 2007-06-20
> **david_edmundson said:**
> Actually there is a better way to do that particular function. What you're doing is waiting till it all loads then changing the value via a script (which is a perfectly valid technique). A better solution is to just  to make it load the correct default. (this is done by root at load time so permissions aren't an issue)

Do this by adding a line to /etc/sysctl.conf
devices.platform.applesmc.fan0_minimum_speed=5000

check all is good by running
cat /sys/devices/platform/applesmc/fan0_minimum_speed after a reboot

Full manual on this is at the usual place (type "man sysctl.conf" in a terminal)

There's no way you'd be expected to know this as a LInux user, it's just something I learnt from asking a very similar question on a mailing list.

at first I was doing this via /etc/rc.local. I tried your suggestion and it didn't do anything. that key isn't even listed when I run `sysctl -A`

and when trying to do it manually in the terminal I get this
```
$ sysctl devices.platform.applesmc.fan0_minimum_speed=5000
error: "devices.platform.applesmc.fan0_minimum_speed" is an unknown key
```

also 5000 seems pretty noisy. is there a tool that monitors fan speed in OSX so one could record average fan speed for a better default?

---

### Post by Rui Pais on 2007-06-20
hi again.
Well, in order to sysctl be used, the kernel must understand (have support for) that instruction. That changes from kernel to kernel, and options selected at compile time... 

About 5000, i don't know Apples but 5000 rotation p.m. looks more like a airplane motor, lol. 

Mine, Intel C2C, are: ~900 cpu fan and ~1900 box. Quiet and calm. temps<30º.

Try to install some temps sensors. Reduce the values for fan until you though temps are still safe and comfortable. 
(In my box i concluded that, except at summer, the chassis fan only serve to do noise, temps don't change either is in maximum rpm continuously or completely turned off.)

---

### Post by ivesjd on 2007-06-20
I think its called Core Duo Temp, and it monitors fan speed and proc. temp in OS X. 
What I did to set the min fan speed is ```
sudo nano /sys/devices/platform/applesmc/fan0_minimum_speed
``` and then entered the minimum speed I wanted. Im not sure if this will keep over a reboot, but it should.

---

### Post by Rui Pais on 2007-06-20
> **ivesjd said:**
> I think its called Core Duo Temp, and it monitors fan speed and proc. temp in OS X. 
What I did to set the min fan speed is ```
sudo nano /sys/devices/platform/applesmc/fan0_minimum_speed
``` and then entered the minimum speed I wanted. Im not sure if this will keep over a reboot, but it should.

Hi, 
no, /sys/ it's a virtual directory. It's filled when kernel boot and it's emptied when you power down. 
Again, rc.local can be used to give that command/value each time you boot.

hth

---

### Post by ivesjd on 2007-06-20
Thanks that worked, then I created an alias of fanspeed for cat /sys/devices/platform/applesmc/fan0_actual_speed. So now I just type in fanspeed is itll read out my fan speed :)

---

