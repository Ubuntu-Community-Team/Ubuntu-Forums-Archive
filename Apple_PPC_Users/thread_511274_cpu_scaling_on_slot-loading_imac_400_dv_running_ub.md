---
title: "cpu scaling on slot-loading imac 400 dv running ubuntu 6.10?"
date: 2007-07-27
forum: Apple PPC Users
---

### Post by badcloud on 2007-07-27
is it at all possible to accomplish this via software without having to tinker with the hardware?

I've tried installing various cpu/battery/temp. monitor/scaling daemons such as powersave, emifreq, and powernowd with no aparent success

what I'd like to do is be able to scale down the cpu in order to prevent overheat after leaving the box idle for long stretches (I have a server running on it that I'd like to keep available 24/7)

I'd appreciate any help at all

---

### Post by stmiller on 2007-07-27
I think powernowd is the way to go at the moment. There was some chatter on the debian powerpc list about some bugs in cpufreq.

Installing powernowd should set things up automagically, though you might want to remove those other daemons which might be conflicting.

So it powernowd is running it should keep the CPU low unless more power is needed.

---

### Post by badcloud on 2007-07-28
thanks for the reply

powernowd doesn't work, rattling off a 4-point complaint list (minimum kernel version, whether or not /sys is mounted, availability of cpufreq and cpufreq-userspace modules, and cpu driver)

1) kernel running now is 2.6.17(-12-powerpc) whereas the minimum required for powernowd is 2.6.7, so I'm guessing I'm in the clear with that one

2) /sys is indeed mounted; result of command > mount | grep sysfs | grep -v grep is
> /sys on /sys type sysfs (rw,noexec,nosuid,nodev), although I'm not exactly clear on what is mentioned within the parentheses

3) I just recently included 'cpufreq-userspace' into /etc/modules but did not reboot to see if it worked, because I could not find 'cpufreq', after running the command 'lsmod | grep cpu'

4) I honestly can't locate my cpu driver

this is the end result of the 'cat /proc/cpuinfo' command:
> processor       : 0
cpu             : 740/750
temperature     : 51-53 C (uncalibrated)
clock           : 400.000000MHz
revision        : 131.0 (pvr 0008 8300)
bogomips        : 49.79
timebase        : 24967326
platform        : PowerMac
machine         : PowerMac2,1
motherboard     : PowerMac2,1 MacRISC2 MacRISC Power Macintosh
detected as     : 66 (iMac FireWire)
pmac flags      : 00000014
L2 cache        : 512K unified
pmac-generation : NewWorld

I'd really like to know whether or not the powerpc g3 processor (specifically the one used by the slot-loading imac 400 dv model) is at all capable of being scaled up or down, because I'd hate wasting your time (not to mention mine and that of anyone else who tries to take a stab at this) resolving all of powernowd's complaints only to find out that the cpu type cannot be scaled by means of software in the first place

---

### Post by ssam on 2007-07-28
i dont think the g3 imacs did frequency scaling, the processor runs pretty cool at full speed

---

### Post by badcloud on 2007-07-28
ok, then how do I at least check if the internal fan is working properly? I don't seem to have the /sys/devices/temperature or fan directory

just for the sake of common knowledge, at which temperature is the internal fan suppose to operate (again, specifically for my imac model) and for that matter, at which temperature am I to expect system shutdown due to overheat?

I've kept my computer on for at least a month and have found it's temp (lucky for me it doesn't have an anus...) to be a steady 51-53 (uncalibrated) with no apparent overheat-related system shutdown. should I be worried if I plan to leave it on for say, half a year?

many thanks for all the feedback (past, present and future)

---

### Post by stmiller on 2007-07-28
It might not have a fan at all. Check out this thread:

[http://forums.macosxhints.com/archive/index.php/t-11672.html](http://forums.macosxhints.com/archive/index.php/t-11672.html)

If it is noisy it is most likely the hard drive making some noise.

I might have to pick one of those up now. I like silent computers. :)

---

### Post by badcloud on 2007-07-28
well then, I'll gladly trade you for whatever computer you have. I prefer them nosiy and cool as apposed to near-silent with a fever

so vat ze hell is supposed to cool off the hardware?!? does software cpu regulation in mac os 8/9 and 10 exist, or is the overall cpu usage generally less than in Ubuntu PPC 6.10 (but last I checked, the System Monitor displayed a total cpu usage of less than 20% while near-idle), making Apple-made machines who wear Apple-made os', cooler, happier babies?

I'm *this* close to buying a buck-and-a-half fan and plugging it to a timed electric circut, and that's not what linux should be about... well, at least that's not what Ubuntu PPC should be about...

yo qiero pancakes! helpo...

---

### Post by stmiller on 2007-07-28
Hey yeah if there's room you can always add in a fan, or buy a fancy heat sink if it will fit as a heat sink upgrade. 
There are low-rpm fans that run quietly and constantly. (I put one in blowing on the video card in my Shuttle box just to keep the video card temp down.)

Sometimes just re-setting the heat sink with a clean application of thermal paste will help too.

---

### Post by badcloud on 2007-07-28
when you wrote fan, did you mean an internal one? I was thinking of buying something to set on the table next to the computer. is there at all room to install an internal fan?

thermal paste on the heat sink? I'll look into it, thanks

---

### Post by stmiller on 2007-07-28
Hey yeah an internal small chipset fan, or something of that size. But well this may be overkill.

---

### Post by badcloud on 2007-07-29
thanks. got me a regular 'external' fan. my imac is basking in cool, retirement linux glory

---

### Post by ssam on 2007-07-29
> **badcloud said:**
> 
so vat ze hell is supposed to cool off the hardware?!? 

The G3 is a very energy efficent chip. all it needs is convection to cool. the iMac has lots of space inside so there is good airflow. i think having the CRT above the CPU is also meant to help draw air upwards.

even running seti@home 24/7 is not trouble for an fanless iMac.

if you are going to point a desk fan at it, make sure you do so as to go with the convection, not against it.

---

### Post by badcloud on 2007-07-29
thanks for the tip, but would it make that much a difference whether or not I pointed the fan against the convection current? the effect of the suction above the convection holes seems to be a lot less potent than the fan blowing against it

the fan managed to cool the previously hot area (around the handle and convection holes) within minutes!

I'm still not sure as to what is overheating in the computer. I spoke to a repair-gal over the phone and she thinks it might be the power supply

---

