---
title: "speed fan/ati tool style app to speed up gpu fan."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-06-28
i need a app for lfiesty that i can speed up my gpu fan speed like i can in ati tool on windows...
what tools are there to do this please.
its urgent as my gpu is sitting around 69-70c atm.

---

### Post by keef247 on 2007-06-29
bump

---

### Post by skymera on 2007-06-29
how about adjusting your cpu speed?

powernowd

```
 sudo apt-get remove powernowd
```

cpudyn


```
 sudo apt-get remove cpudyn
```

    * Step 3: Install CPU Module 

Identify your cpu type by running the command


```
 cat /proc/cpuinfo
```

You can also Check the following links AMD CPU Chart - [[1]] Intel CPU Chart - [[2]]

AMD Sempron/Athlon/MP ( K7 )

Socket Types: A, Slot A


```
 sudo modprobe powernow-k7
```

AMD Duron/Sempron/Athlon/Opteron 64 ( K8 )

Socket Types: 754, 939, 940, S1 ( 638 ), AM2 ( 940 ), F ( 1207 )


```
 sudo modprobe powernow-k8
```

Intel Core Duo


```
sudo modprobe speedstep-centrino
```

Intel Pentium M


```
sudo modprobe speedstep-centrino
```

Intel Pentium 4


```
 sudo modprobe p4_clockmod
```

Others (Unknown)

I'm not entirely sure which cpus are supported using this module. If your cpu doesn't work with one of the above methods try this one.


```
 sudo modprobe acpi-cpufreq
```

    * Step 4: Scaling Modules 


```
sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace
```

    * Step 5: Testing/Configuration 

Show Available Governors


```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

You should see output similar to


```
powersave conservative ondemand performance
```

    * Step 6: Load Modules at Boot 

Add the following lines to the end of /etc/modules


```
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
Also add the module you selected in Step 3
```

    * Step 7: Install cpufrequtils 

This is a simple, effective tool for using the modules from the command line.


```
sudo apt-get install cpufrequtils
```

Test that it's working.


```
 cpufreq-info
```

    * Step 8: Select a governor 

The different governors control how the CPU speed is scaled. Your choices are:

ondemand

CPU frequency is scaled based on load.

conservative

The CPUfreq governor "conservative", much like the "ondemand" governor, sets the CPU depending on the current usage. It differs in behaviour in that it gracefully increases and decreases the CPU speed rather than jumping to max speed the moment there is any load on the CPU. This behaviour more suitable in a battery powered environment.

performance

CPU only runs at max frequency regardless of load.

powersave

CPU only runs at min frequency regardless of load.

See [[3]] for more details.

I typically use ondemand. You get a very slight performance hit and save a lot of power (and produce a lot less heat when idle).

Try it out:


```
 cpufreq-set -g ondemand
```

On systems with more than one CPU you need to repeat the last command for every other CPU you have with specifying the parameter -c (CPU). To set the governor for the second CPU write:


```
cpufreq-set -c 1 -g ondemand
```

To see how many CPUs you have type:


```
 ls /sys/devices/system/cpu/ 
```

    * Step 9: Configure cpufrequtils to automatically set this governor on boot 


```
 Edit the file /etc/default/cpufrequtils. Change the line:

ENABLE="false"

to

ENABLE="true" 
```

Set the GOVERNOR value to the governor name you chose in Step 8. 


_______________________________________________________________________________________

To check your CPU temps. (individual Cores)

```

sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp

```

hope it helps.

i got the info from [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by keef247 on 2007-06-29
I don't get what your saying? apply the same process for gpu or what?
sorry.

---

### Post by chronic on 2007-06-29
what gfx card are you using? 

because 70c isn't considered high. you will be aright as long as you don't exceed the threshold temperature. don't forget that you will be shortening the life of the fan and in turn your gfx card. unless you are going over or close to your threshold temperature don't bother forcing the fan at 100%. 

unfortunately i don't know of any apps that will do this under linux though.

---

