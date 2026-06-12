---
title: "Macbook air cpu throttling"
date: 2011-10-13
forum: Apple Hardware Users
---

### Post by WasabiVengeance on 2011-10-13
I just got a hand me down 1st gen macbook air, and promptly threw Oneiric on it. Everything is running beautifully, but REALLY hot.

I've got a couple scripts that I've used for years to manage my cpu governor, one called getgov and one called setgov. getgov is here:
#!/bin/sh
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

setgov is here:
#!/bin/sh
if [ $# -eq 1 ]
then
	echo $1 | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
	echo $1 | sudo tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
else
   echo "Usage: setgov [conservative,ondemand,userspace,powersave,performance]"
fi

Pretty basic, right?  Well, I'm setting my governor to powersave, if I cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq, it lists my freq as 800000, which I believe is the lowest speed this model supports.

And yet, it's running hot as hell. Estimated battery life is 43 minutes, versus around 150 minutes under osx (yeah, it's pretty heavily used).

Is there some additional quirk to cpu throttling on the air? or on mactels in general?

---

