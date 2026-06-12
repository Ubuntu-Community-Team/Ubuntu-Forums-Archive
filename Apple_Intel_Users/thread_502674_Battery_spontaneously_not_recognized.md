---
title: "Battery spontaneously not recognized"
date: 2007-07-16
forum: Apple Intel Users
---

### Post by kainrcir on 2007-07-16
As per the title, my once working battery now always reports 0%.  I only just noticed this, but to my knowledge it was working fine after the latest updates, and stopped working completely at random.  

$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mW
remaining capacity:      0 mWh
present voltage:         0 mV

$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         0 mWh
last full capacity:      0 mWh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            
OEM info:                

I've tried the fix [here,]("http://ubuntuforums.org/showthread.php?t=457417") even though Im pretty sure this was working after upgrading to 2.6.20-16.  Any suggestions?

---

### Post by kainrcir on 2007-07-17
Fixed it by [resetting the SMC to factory defaults]("http://docs.info.apple.com/article.html?artnum=303319"), if anyone else is having a similar issue

---

### Post by rockstarmode on 2008-01-08
Been a lurker here for a long time and gleaned tons of good info but this post was SO HELPFUL that I registered so I could add a few things.  

I've had this issue on my 2.33Ghz C2D 15" MacBook Pro using Debian stable/unstable and Fedora 7/8.  My symptoms were slightly different:
* When not on AC power gnome-power-manager always reported the battery as 100% charged
* Under Fedora 8 the alarm, info and state files in /proc/acpi/battery/BAT0/ had nothing in them.

Resetting the SMC info as detailed by the Apple doc in the previous post cleared everything up!  I'm pretty sure I NEVER would have found the solution to this problem on my own, thanks so much!

---

