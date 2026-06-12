---
title: "Battery Recognized but Status  not Updated"
date: 2013-01-16
forum: Apple Hardware Users
---

### Post by theverbalninja on 2013-01-16
Initially my battery wasn't recognized at all. I used 
sudo modprobe pmu_battery
 
[FONT=Arial]and added the line[/FONT]
 
pmu_battery
[FONT=Arial] 
to etc/modules. My battery indicator applet is now present, but doesn't always seem to recognize a change in the battery.
On startup, the battery status usually seems to be correct, whether unplugged/plugged in charging/not, but if the computer has been on for a while and then I unplug it, the applet doesn't seem to indicate a change in status.
Thoughts?
[/FONT]

---

