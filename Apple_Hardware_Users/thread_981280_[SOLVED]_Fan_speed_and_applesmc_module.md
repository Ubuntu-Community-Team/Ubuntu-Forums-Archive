---
title: "[SOLVED] Fan speed and applesmc module"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by hyperboloid on 2008-11-13
Does anyone know how I can check if the fan control actually works? My understanding is that the fans are controlled by the "applesmc" module, at least for my model, a MBP 4,1 running the release version of Intrepid with Gnome. 

The minimum fan speed settings in /sys/devices/platform/applesmc.768/fan1_min and /sys/devices/platform/applesmc.768/fan2_min are 2000, and indeed the fans seem to run at that speed every time I check. Most of the time, these settings provide very adequate cooling, and in fact the box seems to run somewhat cooler under Intrepid than it did under OSX. :)

However, I noticed when doing a massive math computation, with one of the CPUs at 100% for 5 minutes or more, that the fans never increased even though the sensors temps went up quite a bit, and indeed the case became much warmer to touch. The core temps did not appraoch the danger threshold, but they became roughly twice as high as "normal" (58 C vs 28 C). 

Isn't applesmc supposed to increase fan speed automatically when things start heating up? I have yet to see that happen on my box: thus my concern. Does anyone know of a way to test the fan control? Or am I misunderstanding the situation?

---

### Post by kosumi68 on 2008-11-13
Did you check this thread: [http://ubuntuforums.org/showthread.php?t=969183](http://ubuntuforums.org/showthread.php?t=969183)

There is also a LP bug about it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550)

---

### Post by hyperboloid on 2008-11-13
> **kosumi68 said:**
> Did you check this thread: [http://ubuntuforums.org/showthread.php?t=969183](http://ubuntuforums.org/showthread.php?t=969183)

There is also a LP bug about it: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262550)

Thanks for the pointer. I skipped that thread because it was tagged for MBP 5,1 and I have 4th gen, but I should have looked at it - it is interesting. I was especially interested in your experiment:

[QUOTE=kosumi68]
I just ran a little experiment on my MBA.

With fan1_manual set to zero, I put the CPU governor to full throttle, then start a kernel compilation. Checking with sensors, the CPU temp quite quickly reaches 80 degC. At this point, the fan speed starts to increase, and after a while reaches the peak 6200 rpms. The CPU temp stays around 80 degC. Now, I stop the compilation, turn the CPU governor to power save, and watch the sensors. The CPU temp very quickly drops to 60 degC. After a couple of minutes, the fan speed slowly drops back to its idling value of 2500 rpms, leaving the CPU at 50 degC.

Now I switch the fan1_manual to one and repeat the process. The temperature reaches 80 degC, but the fan speed stays at 2500 rpms. I watch the temperature reach 85 degC, then I switch fan1_manual back to zero, and abort the experiment. The fan immediately runs up to 6200 rpms, and then slowly returns as the CPU gets cooler.

So, for those that have reported high temperatures due to low fan speeds: check the value of
```
 
cat /sys/devices/platform/applesmc.768/fan1_manual

```
With no software control of the fans, which is the case with the macbooks (fancontrol and pwmconfig does not work), the fan speed seems to be controlled automatically by the SMC without issues - but only if fan1_manual is zero.

Maybe the problem occurs when moving between OSX and Ubuntu via a reboot, which does not clear the NVRAM registers, but this is just a guess.
[/QUOTE]

My fan1_manual = 0 so I'm probably OK. I will have to run your experiment on my box to see if things are working though. It seems that I did not get the temp high enough yet to see the fans kick up their speed, since I have not approached 80 deg C yet.

---

### Post by _mario_ on 2008-11-14
> **hyperboloid said:**
> Does anyone know how I can check if the fan control actually works? My understanding is that the fans are controlled by the "applesmc" module, at least for my model, a MBP 4,1 running the release version of Intrepid with Gnome.c

I think the fans are controlled by hardware. The applesmc module only allows to change the relevant hardware properties (min/max), as long as you don't use *_manual to force a specific speed.

> **hyperboloid said:**
> 
However, I noticed when doing a massive math computation, with one of the CPUs at 100% for 5 minutes or more, that the fans never increased even though the sensors temps went up quite a bit, and indeed the case became much warmer to touch. The core temps did not appraoch the danger threshold, but they became roughly twice as high as "normal" (58 C vs 28 C).

I think this is not a big issue. During my experiment on the same machine, I obversed that the fans start quite late (hysteresis) and 58 °C is not very hot. Try to run cpuburn twice while running the compiz benchmark (or something else requiring graphics) and you'll see (and hear ;-)) the difference. However, if you're concerned about the temperature what about setting the minimum speed to 3000 or 4000 RPM?

ciao,
Mario

---

### Post by cyberdork33 on 2008-11-16
If it seems to run cooler under Ubuntu than OSX, I'd actually suggest decreasing the minimum just a bit to save some power...

80C is not too much to be that concerned. It is warm, but not exceedingly hot. I do like to try and keep my machines in the 70s though if I can.

---

### Post by hellmitre on 2009-03-08
My Macbook Pro 3,1 (running intrepid) has the applesmc module installed but my CPU idles at around 58*C. It gets up to 98*C (eep!) when running two CPUburn processes. Fans kick up to 6000 RPM after a the processor spreads its heat around to surrounding sensors and the average temperature goes up. How do I get it to cool faster? I'm also running the script linked [here]("https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl") (wiki.ubuntu.com), which did help slightly. I'm a tad worried about my processor. Got any ideas?

---

### Post by cyberdork33 on 2009-03-08
> **hellmitre said:**
> My Macbook Pro 3,1 (running intrepid) has the applesmc module installed but my CPU idles at around 58*C. It gets up to 98*C (eep!) when running two CPUburn processes. Fans kick up to 6000 RPM after a the processor spreads its heat around to surrounding sensors and the average temperature goes up. How do I get it to cool faster? I'm also running the script linked [here]("https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl") (wiki.ubuntu.com), which did help slightly. I'm a tad worried about my processor. Got any ideas?
you just need to set the minimum fan speed higher (at the expense of battery life of course)
Like this:
```
echo 6000 > sudo tee -a /sys/devices/platform/applesmc.768/fan1_min
```

---

