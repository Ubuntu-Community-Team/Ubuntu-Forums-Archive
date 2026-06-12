---
title: "Ubuntu 9.10 on PowerPC G4"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by Regunirun on 2010-01-25
Hi, long-time lurker first-time poster.

After being frustrated by slow 10.5 (Leopard), and underpowered 10.4 (Tiger), I decided to try Ubuntu.

Well I got the whole thing working, with all my hardware (to my knowledge) working. 

I also dualboot with 10.5 (Leopard) just-in-case.

There is one problem, however. My battery life.

On OS X I would get ~3 hours per charge (this is a recently replaced battery).

On ubuntu, the battery drains 1% every 30 seconds or so! (Just 50 minutes).

I wonder why this is. I'm something of a Ubuntu noob, so please be specific in your answers.

Suggestions I've had before are disabling a thermal mod (not sure how, not sure why), and dimming the screen...

I suspect, however, that the problem is with Ubuntu not fully "recognizing" my battery, perhaps a single line of text to tell it which one it is would suffice?

Thanks in advance, I'll be happy to clarify if needed.

---

### Post by ditsch on 2010-01-25
I had an issue with the battery in the iBook G4 not recognized. This could be resolved by loading the kernel module pmu_battery manually. The hint came from this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/458004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/458004)

---

### Post by Regunirun on 2010-01-25
Thanks for the response.

I actually already had to add that. Without it, Ubuntu doesn't recognize the battery at all.

---

### Post by ditsch on 2010-01-25
Hm, maybe there is a program permanently using much of the CPU time and therefore also consuming lots of power? Could you check that?

---

### Post by linuxopjemac on 2010-01-25
you can also set the CPU lower with cpufreq (you can add the monitor to your Gnome top panel).
I use the following setup to have powersave default at boot, you might have to only take one, as you don't have two processors:

[http://mac.linux.be/content/set-cpufreq-powersave-boot](http://mac.linux.be/content/set-cpufreq-powersave-boot)

 You can also install cpudyn, which takes care of CPU cycling

[http://mac.linux.be/content/cpu-frequency-scaling-opensuse-111-fix](http://mac.linux.be/content/cpu-frequency-scaling-opensuse-111-fix)

---

