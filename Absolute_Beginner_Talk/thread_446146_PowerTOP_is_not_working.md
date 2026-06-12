---
title: "PowerTOP is not working"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by st33med on 2007-05-16
If you want to know, Intel developed a program that saves processor power and reduces processor wake-up times. More [here]("http://www.linuxpowertop.org/powertop.php").

Anyways, I ran it, and this is the problem I get:
```
Cn          Avg residency (5s)  Long term residency avg
C0 (cpu running)        ( 9.2%)
C1                0.0ms ( 0.0%)                   0.0ms
C2                1.5ms ( 8.5%)                   1.6ms
C3                1.7ms (82.3%)                   1.9ms

[U]No detailed statistics available; please enable the CONFIG_TIMER_STATS kernel option
This option is located in the Kernel Debugging section of menuconfig
(which is CONFIG_DEBUG_KERNEL=y in the config file)[/U]

Suggestion: Enable the CONFIG_NO_HZ kernel configuration option.
This option is required to get any kind of longer sleep times in the CPU.

```

What are the underlined lines talking about?

---

### Post by goandeatsomestuff on 2007-05-16
Do you have kernel version 2.6.21? Unless you have updated your kernel manually, Feisty ships with 2.6.20-15 which doesn't have the required Tickless Idle feature enabled by default, iirc.  

Also, Feisty has several of the PowerTOP enchancements built in to its source, since one of the major contriutors to Intel's project is one of the Feisty code maintainers.

---

### Post by annda on 2007-05-16
> For PowerTOP to work best, use a Linux kernel with the tickless idle (NO_HZ) feature enabled (version 2.6.21 or later). Currently, only 32-bit kernels have support for tickless idle; 64-bit kernels are expected to gain this feature in version 2.6.23.


does your kernel satisfy the conditions?

if not, you may need to recompile your kernel. it's not as scary as it sounds:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by st33med on 2007-05-16
Got me there. It is currently 2.6.20. How do I install the kernel?

---

### Post by annda on 2007-05-16
i'd say wait some time... unless you want to compile it from source.

---

### Post by st33med on 2007-05-16
Why wait? Does the kernel come on update manager after awhile?

---

### Post by annda on 2007-05-16
> **st33med said:**
> Why wait? Does the kernel come on update manager after awhile?

of course! that's why we love ubuntu - some great people compile the stuff, test it and get the best configuration to be useful for all users, package it into nice .deb packages and put it in the repositories.

---

### Post by extremecarver on 2007-05-17
I wouldn't think so. It's two features that are only available on 2.6.21 and would both need backports - but be positive. 
I'm running it on 2.6.22rc1-ck1 with all linuxpowertop patches and phc-centrino (0.2.10 actually supports 2.6.22 too) and can definitely say that there are still a lot of broken software in ubuntu (even with patches I can't get less than 40 interrupts vs 3 that gnome-desktop supposedly needs if well configured) and a seemingly horrible IPW2200 driver/usb-hci which means that with wifi enabled my processor pretty much never enters C3 or C4 state but with wifi disabled I'm nearly 90% C4

---

