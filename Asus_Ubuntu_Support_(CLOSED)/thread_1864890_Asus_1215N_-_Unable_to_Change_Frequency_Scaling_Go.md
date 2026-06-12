---
title: "Asus 1215N - Unable to Change Frequency Scaling Governor"
date: 2011-10-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by skiesbleed on 2011-10-19
Hello all,

I recently got an Asus 1215N, with an Intel Atom D525 processor. I am running Ubuntu 11.04, and I've been trying to get frequency scaling working, since my CPU always runs at full speed, eating up my battery quicker.

I have the frequency scaling indicator in top panel of Unity, and I am able to change the frequency of all cores manually using these values. I can confirm that the clock speed is being adjusted, both by examining /proc/cpuinfo, and by printing /sys/device/system/cpu/cpu<num>/cpufreq/scaling_cur_freq (I think that's what it was) for each core.

The issue, however, is that I cannot use a governor to do this automatically; it will only ever go to Performance, which runs the processor at full speed. When I print out /*sys*/*devices*/*system*/*cpu*/*cpu<num>*/*cpufreq*/scaling_available_governors for each core, I get the following options:

conservative ondemand userspace performance powersaver

However, if I try to set the governor to any of these, either using the cpufreq indicator or by echo the value into /*sys*/*devices*/*system*/*cpu*/*cpu<num>*/*cpufreq*/scaling_governor, the change does not produce any errors, but it immediately switches back to Performance.

Has anyone encountered these issues, and do they have any ideas on how to solve them? I would rather not have to manually scale my processor.

Thanks,

Jack

---

### Post by *nix* on 2011-10-22
> **skiesbleed said:**
> Hello all,

I recently got an Asus 1215N, with an Intel Atom D525 processor.....

[COLOR=Red]I am able to change the frequency of all cores manually using these values[/COLOR]

conservative ondemand userspace performance powersaver  ??????

......back to Performance.

Has anyone encountered these issues, and do they have any ideas on how to solve them? I would rather not have to manually scale my processor.

Thanks,

Jack


Hello

Somewhere read:

 D525 does not support energy-saving technology Speedstep, so it works with 1.8 GHz frequency all the time, using more energy than other Atom processors without a load.

We need to look technical documentation:confused:

There is a possibility:
[COLOR=Red]I am able to [COLOR=SeaGreen]change[/COLOR] the frequency of all cores [COLOR=SeaGreen]manually[/COLOR] using these values[/COLOR]  -  ***good***
 

All the best!

---

### Post by chilloutmo on 2011-12-17
Hello, 

I have the same issue. The processor is always on 1.8ghz in performance mode. the ondemand mode does not work, even when I try to change /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor manually which doesn't work (it won't let me, even with root). With applets I can change manually the core frequency, and powersaver mode works as well, but powersaver is not usable since it scales down to a bit over 200Mhz which freezes the system. 

I would really appreciate if there is a solution to make the ondemand governor work. Since it works in Windows, it does not seem to be a hardware issue.

Thanks!

---

### Post by wollac on 2012-01-04
Have you tried using an app called Jupiter along with the Jupiter eee support package?

---

### Post by foutes on 2012-01-10
The processor in the 1215 is not scalable.

---

### Post by UbuNubi on 2012-01-11
I think this may be the issue I'm having too. I'm not sure. I just installed Ubuntu a couple of days ago (dual booting with win 7) and anytime I'm on Ubuntu, my computer fan is always blowing as though my processor is doing a lot of work or something. The whole entire time I'm on Ubuntu, the fan never stops blowing. When I'm on Win 7, I can't even tell my computer is on most of the time because it's so quiet.

---

