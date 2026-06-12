---
title: "Help with ACPI scripts/events"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by davebed on 2006-11-13
Hi,
I'm 1 month new to Linux and I'm slowly making my way up the ladder.

I have become very interested in the ability to introduce simple scripts into the ACPI directories to control different events and I would love it if someone could introduce me to this subject.

Examples of actions I'd like to be performed are:
1. How to initiate a "screen-off" command by a keystroke (eg. CNTRL + O)
2. How to make the power buttun initiate an auto-hibernation (ie. withough bringing up a menu first)
3. Initiate a command like ```
DISPLAY=:0 /usr/bin/aticonfig --set-powerstate 1
``` during battery state, or equally after, let's say, a resume from hibernate/standby.

I've tried for example putting ```
#!/bin/bash

DISPLAY=:0 /usr/bin/aticonfig --set-powerstate 1

``` into a file called **powersave** and placing it in the battery.d folder, but nothing happens.

I think I'm close on this subject, but missing something and I've had trouble finding info around the forum. 

If you have time, I'd love your feedback.
Many thanks :-D

---

### Post by davebed on 2006-11-14
Could someone at least point me in the right direction? I've been looking around and haven't found this info.

Thanks. <bump!>

---

