---
title: "CPU Scaling on P4"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-06-22
I have Ubuntu working on a P4.  The CPU Scaling applet says "Frequency Scaling Unsupported".  Is that right?  P4 supports frequency scaling doesn't it?

---

### Post by NeoLithium on 2007-06-22
Yes it does :)  There's a nice little howto for CPU Scaling here, that includes P4's [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

---

### Post by weaver4 on 2007-06-22
Now I got a mess.

I went through this process and now my 3.2GHZ processor is stuck at 1.2GHZ.

If I run cpu-info I get this:

  current policy: frequency should be within 1.20 GHz and 1.20 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.

The  frequencies are:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
400000 800000 1200000 1600000 2000000 2400000 2800000 3200000 

And the goveners are:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
userspace powersave ondemand conservative performance 

And the text for my /etc/default/cpufrequtils is:
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=400000
MIN_SPEED=3200000

But when I boot the "CPI Scaling Monitor" says 1.2G

---

### Post by NeoLithium on 2007-06-22
Which module did you modprobe and enter into your /etc/modules file?

---

### Post by weaver4 on 2007-06-22
I forgot to mention that the CPU Frequency Scaling Monitor says the mode is Powersave; 1.2GHZ (37%).

Here are the lines I added to the modules file:

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
p4_clockmod

Here is the /proc/cpuinfo file:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 9
cpu MHz         : 1200.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5551.30
clflush size    : 64

---

### Post by 5-HT on 2007-06-22
> **weaver4 said:**
> I forgot to mention that the CPU Frequency Scaling Monitor says the mode is Powersave; 1.2GHZ (37%). 
That's the normal behaviour for cpufreq_powersave. The clock speed will jump up when required. If you want it at the max all the time,  cpufreq_performance will do the trick (config had ondemand which is similar to conservative in stepping behaviour, albeit with some differences).

cheers,

---

### Post by NeoLithium on 2007-06-22
Ondemand is usually where it will slowly speed up your clock speed as it's needed. If you want the full amount of the processor, set it as:

sudo cpufreq-set -g performance

 :)

Check out cpufreq-set --help for more information, it even lets you set your own hard values :)

---

### Post by weaver4 on 2007-06-22
But that is the problem, I do have it set for ondemand:

And the text for my /etc/default/cpufrequtils is:
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=400000
MIN_SPEED=3200000


But it comes up as PowerSave.

I want it to come up as ondemand not powersave!

---

### Post by NeoLithium on 2007-06-22
So do this:
```
sudo cpufreq-set -g ondemand
```

That will set it for now. The cpufreq default setting is for when you boot the computer up.  Should get you back and ready to fly happily :)

---

### Post by 5-HT on 2007-06-22
I had a similar problem trying to use the powersave governor (it was defaulting to ondemand despite powersave being selected in the configs). 

Here's a dirty little hack:
Blacklist the powersave governor module (echo "cpufreq_powersave" | sudo tee -a /etc/modprobe.d/blackist)

Is ondemand being used then?

---

### Post by weaver4 on 2007-06-22
I am rebooting everytime.  And it still comes up as powersave.

Even when I run the command you just gave I get the followin on cpufreq-info.

 current policy: frequency should be within 1.20 GHz and 1.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.

So it says it ondemand but ignores my frequency choices and sets it to 1.2GHz.

---

### Post by 5-HT on 2007-06-22
> **weaver4 said:**
> I am rebooting everytime.  And it still comes up as powersave.

Even when I run the command you just gave I get the followin on cpufreq-info.

 current policy: frequency should be within 1.20 GHz and 1.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.

So it says it ondemand but ignores my frequency choices and sets it to 1.2GHz.

Meh :(. Could be the p4, are you using the p4_clockmod module for it, or acpi_cpufreq? p4_clockmod is quite limited, but it may be your best bet if acpi_cpufreq isn't working. speedstep_centrino is deprecated and should not be used.
One thing to try: max out your CPU and see if the frequency jumps.
Another thing to try and avoid hassles would be to give powernow a try (it's in the repos). It's a userspace agent that won't use the kernel throttling modules and you won't have to worry about the config.

---

### Post by weaver4 on 2007-06-22
Black listing did not work.

I am using p4_clockmod. 

I tried maxing out the CPU and it does not move off of 1.2Ghz.

---

### Post by weaver4 on 2007-06-22
I installed powernowd (which uninstalled cpufreq) and now it appears to be working correctly.

Thanks for your help.

---

### Post by Talon2 on 2007-06-23
> **weaver4 said:**
> 
And the text for my /etc/default/cpufrequtils is:
ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=400000
MIN_SPEED=3200000

But when I boot the "CPI Scaling Monitor" says 1.2G

Should it read:

MAX_SPEED=3200000
MIN_SPEED=400000

Actually I use MIN_SPEED=1600000 because 400000 causes things to be a little sluggish.

---

### Post by jester261 on 2007-07-19
Hi i have **Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz **cpu and after i entered  to the terminal [COLOR="Black"]**sudo modprobe p4_clockmod**[/COLOR] it only displays this error  [COLOR="Red"]**FATAL: **[/COLOR][COLOR="Red"]**Module p4_clockmode not found.**[/COLOR]. Can somebody help me?

---

