---
title: "Did tickless enabled in Gutsy?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by drivel on 2007-10-06
Hi,guts,but I'm not very clearly about weather Tickless was enabled in Gutsy.
Anyone got answers?

---

### Post by shae on 2007-10-06
If you are using Gusty run this:
```
cat /boot/config-$(uname -r) | grep CONFIG_NO_HZ
```

If the output is 
CONFIG_NO_HZ=y
then you do have a tickless system.

If the output is
CONFIG_NO_HZ=n
then you do not have a tickless system.

---

### Post by drivel on 2007-10-07
> **shae said:**
> If you are using Gusty run this:
```
cat /boot/config-$(uname -r) | grep CONFIG_NO_HZ
```

If the output is 
CONFIG_NO_HZ=y
then you do have a tickless system.

If the output is
CONFIG_NO_HZ=n
then you do not have a tickless system.

Thanks,buddy.

cat /boot/config-$(uname -r) | grep CONFIG_NO_HZ
CONFIG_NO_HZ=y

Enabled...:guitar:

---

### Post by LowSky on 2007-10-07
what is tickless? and yes mine is eabled

---

### Post by tgalati4 on 2007-10-07
I believe a tickless kernel does not schedule tasks based on a millisecond "tick".  Instead tasks remain running until another task needs to be executed.  This means that sleeping tasks stay asleep and are not waken because the tick timer says I have to touch you every 25 milliseconds.

This supposedly gives a performance boost because you have between 100 and 200 tasks running in a modern Linux system.  Most of them are sleeping and should remain asleep unless some event requires them wake up.

I have yet to see some benchmarks, but I'm sure they are out there.

---

### Post by bitwiseshiftleft on 2007-10-13
A normal kernel sets off a timer interrupt every 4ms or so, at which point it checks whether new tasks need to be scheduled.  A tickless kernel instead computes when new tasks will need to be scheduled, and sets a timer interrupt for then.  There won't be a noticeable performance increase from this, but it means your processor gets to sleep for longer (particularly when the system is idle), so it will consume less power.

---

### Post by bobpaul on 2007-10-16
I'm running the 64bit Gutsy beta. Kernel 2.6.22-14-generic. AFAICT, tickless wasn't even a build option for my kernel.

```
$ cat /boot/config-$(uname -r) | grep CONFIG_NO
CONFIG_NODES_SHIFT=6
# CONFIG_NORTEL_HERMES is not set
```

I thought this was one of the major new features in Gutsy. A lack of tickless is upsetting, and indeed powertop keeps telling me to enable it as a "TIP." Does anyone know if powertop checks for the actual kernel ability, or if it only checks the config-* file that matches the running kernel version?

---

### Post by shae on 2007-10-16
Tickless is not yet available for 64bit systems.  Look for this feature in 2.6.23 IIRC.

---

### Post by bobpaul on 2007-10-16
So probably not until Hardy Heron, then?

---

### Post by shae on 2007-10-16
Yes, unless you compile your own kernel.

---

### Post by FredB on 2007-10-16
> **shae said:**
> Tickless is not yet available for 64bit systems.  Look for this feature in 2.6.23 IIRC.

What a pity I am using an AMD64 version ! :lolflag:

---

### Post by edrex on 2007-11-29
CONFIG_NO_HZ isn't set on my gutsy kernel either:
```

$ cat /boot/config-$(uname -r) | grep CONFIG_NO_HZ
  # CONFIG_NO_HZ is not set
$ uname -r
  2.6.22-14-386
```
Those who are reporting that it is, what kernel are you running? Generic perhaps? 

I suppose the UME kernel will be getting the most power-savings optimizations going forward, may be worth checking out if you have a mobile.

---

### Post by edrex on 2007-11-29
Ok, I installed generic and see that CONFIG_NO_HZ is on! Good to see serious effort to make Linux more efficient!

---

### Post by MozartlovesUbun2 on 2007-11-30
so if this saves power, is it now on by default in laptops?

thanks

---

### Post by shae on 2007-11-30
It is default if you use the generic kernel in gutsy, 32bit version that is.  In Hardy it will be default for both 32 and 64 bit.

---

