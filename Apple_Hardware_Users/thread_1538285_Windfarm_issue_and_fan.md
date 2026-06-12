---
title: "Windfarm issue and fan"
date: 2010-07-24
forum: Apple Hardware Users
---

### Post by selittl on 2010-07-24
Ok, noob question.  I understand that my haywire fans in my iMac G5 are an issue with the Windfarm drivers.  I need to know how to compile/build the available driver and install it on my machine.  Can someone please help?

Thanks!

---

### Post by imrazor on 2010-07-24
> **selittl said:**
> Ok, noob question.  I understand that my haywire fans in my iMac G5 are an issue with the Windfarm drivers.  I need to know how to compile/build the available driver and install it on my machine.  Can someone please help?

Thanks!

Try ```
sudo modprobe windfarm_core
``` and see what happens. If that works, add a line ```
windfarm_core
``` to /etc/modules.

---

### Post by selittl on 2010-07-25
Nothing happens.  At startup I get error codes concerning windfarm.  If I knew of a way to screen capture them I would.

---

### Post by imrazor on 2010-07-25
> **selittl said:**
> Nothing happens.  At startup I get error codes concerning windfarm.  If I knew of a way to screen capture them I would.

OK, check to see if it loaded successfully.After running ```
sudo modprobe windfarm_core 
```, then see if the module loaded by running ```
sudo lsmod | grep -e windfarm
``` If you get output from the above command, then the module loaded successfully. Also make a note if any other windfarm modules besides windfarm_core loaded. 

modprobe doesn't give any output when it's succesful, so a result of "nothing" may be the right one. If your fans are still running, you might need to give windfarm a few minutes to kick in. It might also be necessary to manually load the remaining necessary windfarm modules, though it may take some research to figure out which ones you need. They are there on Ubuntu, but may not be loaded. One of them is loading on my Powermac and causing it to crash, so they're definitely present.

---

### Post by selittl on 2010-07-25
OK, this is the output I get 

windfarm_smu_sensors     8567  2 
windfarm_smu_controls     7629  0 
windfarm_max6690_sensor     5588  0 
windfarm_lm75_sensor     6091  0 
windfarm_smu_sat        8496  0 [permanent]
windfarm_cpufreq_clamp     3805  0 
windfarm_pid            3553  0 
windfarm_core          15947  6 windfarm_smu_sensors,windfarm_smu_controls,windfarm_max6690_sensor,windfarm_lm75_sensor,windfarm_smu_sat,windfarm_cpufreq_clamp

What is this telling me?

---

### Post by imrazor on 2010-07-25
> **selittl said:**
> OK, this is the output I get 

windfarm_smu_sensors     8567  2 
windfarm_smu_controls     7629  0 
windfarm_max6690_sensor     5588  0 
windfarm_lm75_sensor     6091  0 
windfarm_smu_sat        8496  0 [permanent]
windfarm_cpufreq_clamp     3805  0 
windfarm_pid            3553  0 
windfarm_core          15947  6 windfarm_smu_sensors,windfarm_smu_controls,windfarm_max6690_sensor,windfarm_lm75_sensor,windfarm_smu_sat,windfarm_cpufreq_clamp

What is this telling me?
lsmod generates a list of every kernel module loaded on your system. 'grep -e windfarm' filters the output to only show the windfarm modules that are loaded and  running.

If your fans are still running with all the windfarm modules loaded, that may point to a hardware problem. Do you have OS X loaded on this Mac? Do the fans run normally under OS X? What do you get from this command: ```
cat /proc/device-tree/model
``` The above command will tell us specifically what model of iMac you're running. I believe windfarm is compatible with all models of G5 iMac, but I could be wrong.

---

### Post by frogger78 on 2010-08-25
[FONT=Arial]I'm having issues with this too.  Got the[/FONT][FONT=Arial] same output as [/FONT][FONT=Arial]selittl.[/FONT]

First my fans were running non stop, now after a few attempts at fixing them, they aren't running at all and this comp is running at about 160 degrees F

---

### Post by egalois on 2010-09-10
Hi imrazor

I had the same issue. 

```
nicolas@ubuntu:~$ sudo modprobe windfarm_core
[sudo] password for nicolas: 
nicolas@ubuntu:~$ sudo lsmod | grep -e windfarm
windfarm_smu_sensors     8567  2 
windfarm_smu_controls     7629  0 
windfarm_max6690_sensor     5588  0 
windfarm_lm75_sensor     6091  0 
windfarm_smu_sat        8496  0 [permanent]
windfarm_cpufreq_clamp     3805  0 
windfarm_pid            3553  0 
windfarm_core          15947  6 windfarm_smu_sensors,windfarm_smu_controls,windfarm_max6690_sensor,windfarm_lm75_sensor,windfarm_smu_sat,windfarm_cpufreq_clamp
nicolas@ubuntu:~$ cat /proc/device-tree/model
PowerMac12,1nicolas@ubuntu:~$

```

But unfortunately after reboot, my fan went at high speed again. Do you know a solution for this problem. As you can imagine this noise is annoying. I'm thankful for every possible solution!
Just for completeness: I'm running Ubuntu 10.04 on a iMac G5 1.9 GHz (Rev C) with 1GB RAM.

cheers egalois

---

### Post by imrazor on 2010-09-11
Egolais-

Your issue appears to be different from what I was experiencing. I was seeing only ONE of the windfarm modules loaded, specifically windfarm_core, which seemed to be conflicting with power management module specific to my Powermac model (Powermac8,7 or something like that.) If I get a chance, I'll post my specific model sometime later today. Only two very specific models of Powermac and one model of iMac are affected, and the affected models only load ONE windfarm module. As well as my fix has worked for me, I doubt it'll do you any good given that you have loaded all of the above modules.

Sorry I can't help you out with this, but it looks like we both have different scenarios. If you still have OS X, you can try looking up your Powermac model in System Profiler and we can compare notes.

---

### Post by roberto.tomas on 2010-10-18
> **imrazor said:**
> If your fans are still running with all the windfarm modules loaded, that may point to a hardware problem.

Is it possible that fans would run too high on a Quad G5? I have been searching and found many articles talking about having to patch the code to recognize two physical processors, and my fan speeds have always been high both on 10.04 and now on 10.10.

Also, is there a way to custom configure the base fan speed (which currently is apparently about 1000 rpm on the cpus)? I feel left in the dark about how this subsystem works since ubuntu uses a custom package instead of the normal unix sensors package.

---

