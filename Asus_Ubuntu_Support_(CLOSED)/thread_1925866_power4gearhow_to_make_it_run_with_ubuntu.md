---
title: "power4gear:how to make it run with ubuntu"
date: 2012-02-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ntl on 2012-02-15
Hello,

I have an ASUS K53SV with double boot (win 7 + ubuntu 11.10). In windows with power4gear  I choose "quiet office" to avoid the fan's noise. I have no idea about how to do it in Ubuntu, reading the forums I have tried to install ironhide following the instructions from [www.ivegotavirus.com/blog/2011/09/01/how-to-set-up-intel-optimus-graphics-on-ubuntu-save-battery-life/]("http://ubuntuforums.org/www.ivegotavirus.com/blog/2011/09/01/how-to-set-up-intel-optimus-graphics-on-ubuntu-save-battery-life/"), but I'm not very sure if I have done it right (fan still running) and I don't know how can I check it either.

Can somebody help me to get the same I get with power4gear in windows? Thanks.

---

### Post by ntl on 2012-02-16
I have found out that power4gear manage among other things:


[LIST=1]
[*]Battery saving desktop
[*]Intel DPST control
[*]System cooling policy (active/passive fan)
[*]Wireless adapter configuration: Battery save mode
[*]Intel graphics settings: power plan (maximum battery life...)
[*]PCI express: Link state power manage
[*]CPU power manage
[*]Internet explorer: Java script timer frequency power plan (I don't know if there is something like that in Firefox)
[*]Video: optimise quality/save/balance
[/LIST]
I have google and find that CPU power manage can be added to ubuntu's taskbar, so that should be solved (I have not tried it). I have no idea about how to manage the other options, I'm specially interested in the system cooling policy, since I want to avoid noise.


I'll be very thankful if someone could help me with these issues.

---

### Post by xycris on 2012-04-01
i am also looking for a power4gear alternative for my asus unit.

i was able to find some though i am afraid to implement because they are still in experimental stage and i don't have the luxury to experiment at this time for the community.

but you can try them compiled here:
[http://www.lesswatts.org/](http://www.lesswatts.org/)

---

### Post by ntl on 2012-04-09
Thank you xycris, I'm quite new to Linux, but I'll try to experiment something from  the link you send and see if it works. If you finally find out an alternative ASUS please let me know.

---

### Post by xycris on 2012-08-07
no problem ntl.

i am running an asus lappy and really find it very draining to use the ubuntu especially when upgraded to 12.04 while on batteries for it last only a couple of minutes after running for an hour. while in windows the lappy can reach up to 5hours on battery (10 hours if not frequently used).

i also noticed that the lappy is even hotter when in ubuntu keeping the fan up all the time adding to the noise aside from the excessive heat.

what solved my problem is by installing cpu frequency scaling indicator and psensor+lm-sensor+xsensor. just google on these stuffs (works great in ubuntu 12.04).

hope that helps in your power4gear hunt and also if you have asus probe support into your hardware.

---

### Post by ntl on 2012-08-07
Thanks xycris.

I have install cpu-freq indicator with no problem, hope it will work (I think that power4gear's "secret" was that, the quite office mode uses just 70%).

I have installed the psensors etc.  too, but I don't know why it just shows the temp of cores from 0 to 4, while the lap has 7 cores. No idea about how to fix this. 

I tried to search in the BIOS if there was a "cool and quiet" like options but I did not find enaything similar.

Hope your lap is working better (and hope mine will do too!).

---

### Post by venky96 on 2012-08-15
You could use "Jupiter" which is somewhat like power4gear. It changes CPU frequency to save battery. But generally with lower frequency you attain lesser noise. It also has extra support for Asus EeePC and Supports Asus Super Hybrid Engine. 

[http://refugeeks.com/RefuGeeks/2012/06/make-your-batter-last-longer-in-ubuntu-with-jupiter/]("http://refugeeks.com/RefuGeeks/2012/06/make-your-batter-last-longer-in-ubuntu-with-jupiter/")

Hope that helps

---

### Post by ntl on 2012-10-01
Hi venky96,

I have been using cpufreq, you can choose an exact GHz or powersave/ondemand... Choosing powersave or ondemand or low GHz there has been little noise, until now!! (Maybe an update has changed comething...). I suppose that Jupiter is something similar to cpufreq, but I'll try it and see if it makes a difference. Thanks!

---

### Post by pompel9 on 2012-10-01
Thank you for the tip on jupiter. I have installed it, I will post here if I find some problems with it.

---

### Post by Linuxisfast on 2012-10-17
The 12.04 kernel has got some extensive work done on power management and usually both my ASUS laptop and netbook last close to Windows time and also the temps are well under control as long as I install and keep the proprietary video drivers updated. I haven't seen that much improvement with Jupiter.

---

### Post by xycris on 2013-01-22
My lappy is now performing better with 12.10 but I still have cpufreq up and running.

The temp rising I am experiencing now might be the limits of the processor and gpu with higher minimum wattage rates. It is the same performance whether Windows or Ubuntu.

Cheers!

(Hope this can be flagged solved if everything is already fine)

---

### Post by ntl on 2013-01-23
I'm running 12.04 too, using cpufreq and no proprietary drivers. I usually choose "conservative" or "powersave", the fan turns on more times than using power4gear on windows, and windows still is more quite than ubuntu with cpufreq. I have not checked the battery length.

---

