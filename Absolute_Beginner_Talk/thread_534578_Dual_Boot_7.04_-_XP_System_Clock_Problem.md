---
title: "Dual Boot 7.04 - XP System Clock Problem"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by jay_y on 2007-08-25
I dual boot 7.04 and XP, everything works great other than Ubuntu resets system clock ahead 4 hours.  Ubuntu displays correct time but XP is +4 Hours.  Any ideas ?

---

### Post by krazytekn0 on 2007-08-25
I'd check  your time zone in XP... Ubuntu is probably right, and XP may have you under a different time zone and this could be causing your problem.

Not absolutely sure, but that's my best guess.

---

### Post by jay_y on 2007-08-25
XP is set to GMT -5 (EST).  Time is right in XP, when I boot 7.04 it sets the system clock ahead.  Is there a setting to stop Ubuntu from touching the system time?

---

### Post by AnotherMuggle on 2007-08-25
> **jay_y said:**
> XP is set to GMT -5 (EST).  Time is right in XP, when I boot 7.04 it sets the system clock ahead.  Is there a setting to stop Ubuntu from touching the system time?

I would be interested to know if a solutions comes up for this one. 

I am running a tripple boot system and XP (not sure about Vista) was getting the time messed for some reason.  Thought it was the motherboard battery at first but a replacement does not appear to have made any difference.

---

### Post by Thelasko on 2007-08-27
Off of the top of my head, try going to adjust date and time and select "UTC."  My guess is one OS is using UTC and the other isn't, therefore there is a discrepancy.

---

### Post by Magneticgravity on 2007-08-27
Hehe, just XP for you :P

---

### Post by schorsch on 2007-08-27
What is the output of
```
cat /etc/timezone
``` under Ubuntu? Are you syncing the system time via ntp?
I guess the reason is that the hardware clock is set to the OS clock when the system shuts down. This is done via the script /etc/init.d/hwclock.sh. When XP starts up it just reads the hardware clock and sets this as its OS time. So you should check (as already mentioned) if there are some differences is the timezones you have defined under Ubuntu and XP.

---

### Post by fallencyi on 2007-08-27
I had the same problem. After reading several threads on this forum here is what worked for me, based on input from others:

sudo gedit /etc/default/rcS


Change:

UTC=yes

to 

UTC=no

---

