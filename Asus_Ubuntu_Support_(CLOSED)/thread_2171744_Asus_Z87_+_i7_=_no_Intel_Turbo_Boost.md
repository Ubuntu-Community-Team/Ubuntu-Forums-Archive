---
title: "Asus Z87 + i7 = no Intel Turbo Boost"
date: 2013-09-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by JD82 on 2013-09-01
[B]TL;DR
[/B]Turbo Boost does not work on Ubuntu 13.04 (kernel 3.10.10), some other i5/i7 owner could help me out with some test?

**Long version**
A few days ago I assembled a new computer (Asus Z87-Deluxe + i7-4770k). Everything seemed to be working properly except the Broadcom wifi card, but I expected that.

Yesterday, however, I realized that the maximum frequency detected by Ubuntu 13.04 is 3501 MHz and not, as it should be, 3901 MHz.

I searched on Google and I made all the steps to enable the Turbo Boost:

[LIST]
[*]I verified that the Turbo Boost was enabled in the bios
[*]I loaded the msr module ([FONT=courier new]sudo modprobe msr[/FONT] and then added to [FONT=courier new]/etc/modules[/FONT])
[*]I compiled and run i7z
[*]I checked out the maximum frequency detected by the kernel (03/10/10)
[/LIST]
i7z confirms that the Turbo Boost is enabled:

```
Cpu speed from cpuinfo 3499.00Mhz
cpuinfo might be wrong if cpufreq is enabled. To guess correctly try estimating
Linux's inbuilt cpu_khz code emulated now
True Frequency (without accounting Turbo) 3499 MHz
  CPU Multiplier 35x || Bus clock frequency (BCLK) 99.97 MHz


Socket [0] - [physical cores=4, logical cores=8, max online cores ever=4]
  TURBO ENABLED on 4 Cores, Hyper Threading ON
  Max Frequency without considering Turbo 3598.97 MHz (99.97 x [36])
  Max TURBO Multiplier (if Enabled) with 1/2/3/4 Cores is  39x/39x/38x/37x
  Real Current Frequency 880.54 MHz [99.97 x 8.81] (Max of below)
        Core [core-id]  :Actual Freq (Mult.)      C0%   Halt(C1)%  C3 %   C6 %
        Core 1 [0]:       880.54 (8.81x)        10.6    80.7    13.4    3.33
        Core 2 [1]:       850.15 (8.50x)        8.88      89    5.51    3.28
        Core 3 [2]:       841.77 (8.42x)        13.2    87.4    6.55    2.92
        Core 4 [3]:       832.13 (8.32x)        11.1    89.5    4.08    3.77

C0 = Processor running without halting
C1 = Processor running with halts (States >C0 are power saver)
C3 = Cores running with PLL turned off and core cache turned off
C6 = Everything in C3 + core state saved to last level cache
  Above values in table are in percentage over the last 1 sec
```
but even at full load, the maximum frequency is struggling to get to 3.5 GHz (full load reached through Geekbench 3).

After further research I found [a Gentoo user with my same problem]("http://forums.gentoo.org/viewtopic-t-898440-start-0.html"). He also found a workaround: use the performance governor.
With this governor Turbo Boost is used (confirmed by i7z and significantly better results Geekbench), but the cores are always at maximum frequency.


On the same forum other people have on their PCs Turbo Boost with the governor set to on demand, so I assumed that it could be a problem specific to my MoBo/BIOS, which does not send the correct information to the kernel. This seems to be confirmed by this output:
```
# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
3501000 3500000 3300000 3100000 2900000 2700000 2500000 2300000 2100000 2000000 1800000 1600000 1400000 1200000 1000000 800000
```

As you can see through the available frequencies, the Turbo Boost is reduced to an increase of 1 MHz ..


Before reporting the matter to the Asus I could really have some more feedback from other owners of i5/i7, can anyone help?

---

### Post by Merrattic on 2013-09-01
I have an Asus Z87M PLUS with i5 4670K

How to capture the ncurses info as text ?

---

### Post by JD82 on 2013-09-01
Thanks for the reply.

I've just quickly selected the text with the mouse and copied with CTRL + SHIFT + C.

Could you please also post the output of ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by Merrattic on 2013-09-01
Won't let me do it! I'll keep trying, but here is

```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
3401000 3400000 3200000 3000000 2800000 2700000 2500000 2300000 2100000 1900000 1700000 1500000 1400000 1200000 1000000 800000 
```

Turbo is on, but Hyper Threading is off

Got it (SHIFT+CTRL+A+C)

```
Cpu speed from cpuinfo 3398.00Mhz
cpuinfo might be wrong if cpufreq is enabled. To guess correctly try estimating via tsc
Linux's inbuilt cpu_khz code emulated now
True Frequency (without accounting Turbo) 3397 MHz
  CPU Multiplier 34x || Bus clock frequency (BCLK) 99.91 MHz

Socket [0] - [physical cores=4, logical cores=4, max online cores ever=4]
  TURBO ENABLED on 4 Cores, Hyper Threading OFF
  True Frequency 3496.91 MHz (99.91 x [35])
  Max TURBO Multiplier (if Enabled) with 1/2/3/4 Cores is  38x/38x/37x/36x
  Current Frequency 2922.63 MHz [99.91 x 29.25] (Max of below)
        Core [core-id]  :Actual Freq (Mult.)      C0%   Halt(C1)%  C3 %   C6 %  Temp
        Core 1 [0]:       2922.63 (29.25x)      13.3    88.5       0       0    32
        Core 2 [1]:       2087.01 (20.89x)      13.5    91.7       0       0    27
        Core 3 [2]:       1647.97 (16.49x)      6.04    97.1       0       0    29
        Core 4 [3]:       1016.31 (10.17x)      4.29    97.7       1       0    29



C0 = Processor running without halting
C1 = Processor running with halts (States >C0 are power saver)
C3 = Cores running with PLL turned off and core cache turned off
C6 = Everything in C3 + core state saved to last level cache
  Above values in table are in percentage over the last 1 sec
[core-id] refers to core-id number in /proc/cpuinfo
'Garbage Values' message printed when garbage values are read
  Ctrl+C to exit
```

---

### Post by JD82 on 2013-09-01
You seem to suffer from the same problem: max available frequencie read by the kernel is 3401000 (should be 3801000).

**EDIT**
I do not know what to say: now it's working. Max available frequencie is always 350100 but now at full load reaches 4.1 GHz:
[IMG]http://i44.tinypic.com/2w1utm1.jpg[/IMG]

This afternoon I updated the BIOS to the latest version released today, but after the upgrade I did a test and did not seem to have changed anything...

If you want to test you can try this application: [http://sourceforge.net/projects/systester/?source=dlp](http://sourceforge.net/projects/systester/?source=dlp)
Since you have an i5 set 4 threads instead of 8.

Let me know and thanks again.

---

### Post by Merrattic on 2013-09-01
OK ran a test at max and got a similar increase to you. Guess you have to push the processor to get the max out of it ?

```
Cpu speed from cpuinfo 3397.00Mhz
cpuinfo might be wrong if cpufreq is enabled. To guess correctly try estimating via tsc
Linux's inbuilt cpu_khz code emulated now
True Frequency (without accounting Turbo) 3398 MHz
  CPU Multiplier 34x || Bus clock frequency (BCLK) 99.94 MHz

Socket [0] - [physical cores=4, logical cores=4, max online cores ever=4]
  TURBO ENABLED on 4 Cores, Hyper Threading OFF
  True Frequency 3497.94 MHz (99.94 x [35])
  Max TURBO Multiplier (if Enabled) with 1/2/3/4 Cores is  38x/38x/37x/36x
  Current Frequency 3609.16 MHz [99.94 x 36.11] (Max of below)
        Core [core-id]  :Actual Freq (Mult.)      C0%   Halt(C1)%  C3 %   C6 %  Temp
        Core 1 [0]:       3599.58 (36.02x)      90.8    3.81       0       0    51
        Core 2 [1]:       3609.16 (36.11x)      97.3       0       0       0    52
        Core 3 [2]:       3604.93 (36.07x)      95.9       0       0       0    50
        Core 4 [3]:       3603.08 (36.05x)      93.6       1       0       0    51



C0 = Processor running without halting
C1 = Processor running with halts (States >C0 are power saver)
C3 = Cores running with PLL turned off and core cache turned off
C6 = Everything in C3 + core state saved to last level cache
```

---

### Post by JD82 on 2013-09-01
Yep, but yesterday it was not working. Perhaps with the BIOS update has changed something.

---

### Post by Merrattic on 2013-09-01
I downloaded the bios update but not got around to it yet, will report back if it makes any difference. 

You also seem to be running quite hot @ 75 degrees? At idle I am at 30 degrees and at full tilt @ 55. This with fan at 1300rpm.

---

### Post by JD82 on 2013-09-02
> **Merrattic said:**
> You also seem to be running quite hot @ 75 degrees? At idle I am at 30 degrees and at full tilt @ 55. This with fan at 1300rpm.

Yes, I know: I have enabled the BIOS auto-overclock and it sets the CPU VCORE to 1.2V. As soon as I can I need to find a manual overclock which does not excessively increase the temperature in full.

At idle, even with this overclock, I am also at 30 degrees.

---

