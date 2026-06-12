---
title: "Graphics Problem- Ended up in low graphics mode"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Drenthe on 2008-03-01
Running Ubuntu 7.10 I've been doing fine on an XPS M1710.... Using Envy to get the nvidia driver working when I initially installed worked perfectly and had been running 1920x1200 for a while now with no problem..

Then today I got myself another Dell LCD monitor and wanted to use it for extra workspace... When I plugged the monitor in I went to "screens and graphics" and wanted to see if it was recognized. The monitor was there as generic with 800x600 resolution... Being impatient I chose the proper resolution monitor out of the drop list there and restarted the computer.... When I rebooted I came up in low graphics mode- and when I try to use 'Nvidia Settings' it tells me I am not using an nvidia driver.... basically the driver is gone and I can't think of what to do...

I have tried to re-run envy to solve the problem but after the restart it's as if nothing was done... The restricted drivers are not enabled upon each restart even if I check it and then restart....

...help...?

I'm assuming I'll be told to run some commands for better help but I have no idea what...

---

### Post by taurus on 2008-03-01
Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Drenthe on 2008-03-01
Fixed with the next thing I tried after I posted this....

ignore.

---

