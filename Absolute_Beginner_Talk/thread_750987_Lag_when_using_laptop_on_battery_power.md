---
title: "Lag when using laptop on battery power"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Kvad on 2008-04-10
Hi all,

I've just done a fresh install of 8.04 on to my Laptop. 

Everything is running fine on AC. But when I switch to using the battery and leave the laptop  idle for a few mins, then try to use it again it will take sometime to respond (mouse movement is sluggish, in general the gui is sluggish). 

This is a fresh install, had the same problem when I upgraded from 7.10.

I am quite sure I didn't have this issue with 7.10 (will install tonight to verify)

PC - 1.7GHZ, 1GB RAM, 80GB HDD  - Dell Inspiron 630m

Any suggestions? Thanks in advance.

*edit*
Maybe I should be posting this in the Hardy Heron section?

---

### Post by warbread on 2008-04-10
This seems perfectly reasonable to me.  When running on battery, your computer should be dynamically changing the clockspeed of its CPU to reduce power consumption.  It may also cut power to USB ports until it detects activity in the devices.  

Try going into the power settings and turning off all of the power saving features and then use it on battery power.  If that changes anything, you can chalk it up to just power management.

---

### Post by formulajay on 2008-05-24
I get a similar problem with my Dell Latitude D610. I am using Ubuntu 8.04 and when I use the laptop on A/C power I have absolutely no problems at all.

The problems happen when I am using the laptop on battery power. If I leave the computer alone, sometimes only for a few seconds, the mouse and keyboard take 5-10 seconds to become responsive again. That is not the most annoying part. After this happens several times, the laptop freezes completely and the Caps Lock light and the Fn Button light flash. I am unable to do anything except a hard restart.

Anyone else with this problem, and more importantly any solutions?

I have gone into the power management settings and set time limit to go into sleepmode to never(on battery power). This has no effect whatsoever.

---

### Post by Steve413z on 2008-05-24
I think that has something to do with the hard drive turning off to save battery life,

/etc/laptop-mode/laptop-mode.conf

should be the place to adjust the setting

---

### Post by Bubba64 on 2008-05-24
Ubuntu Tweak has quick access to changing power usage.

---

