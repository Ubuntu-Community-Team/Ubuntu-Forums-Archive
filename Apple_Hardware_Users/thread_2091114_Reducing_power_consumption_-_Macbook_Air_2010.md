---
title: "Reducing power consumption - Macbook Air 2010"
date: 2012-12-04
forum: Apple Hardware Users
---

### Post by Atomyzed on 2012-12-04
I have Xubuntu installed on a late 2010 Macbook Air (Core 2 Duo + Nvidia 320m GPU). I'm trying to find ways to reduce power consumption, aiming for under 10w when idling.

So far, I've:

- Installed laptop-mode-tools
- Turned off bluetooth
- Reduced the minimum brightness level on the display

However, even after this battery life is quite poor. The output from powertop shows:

```
The battery reports a discharge rate of 11.5 W
The estimated remaining time is 3 hours, 25 minutes

Summary: 213.9 wakeups/second,  0.0 GPU ops/seconds, 0.0 VFS ops/sec and 5.2% CPU

                Usage       Events/s    Category       Description
            100.0%                      Device         Audio codec hwC0D4: Nvidia
            100.0%                      Device         Audio codec hwC0D0: Cirrus
            100.0%                      Device         Audio codec hwC0D3: Nvidia
            100.0%                      Device         Audio codec hwC0D5: Nvidia
              3.0%                      Device         Display backlight
             20.2 ms/s     145.5        Process        /usr/lib/firefox/firefox
             14.0 ms/s      10.3        Process        /usr/bin/X :0 -core -auth
              3.5 ms/s      20.9        Timer          hrtimer_wakeup
              2.7 ms/s      0.00        Interrupt      [0] timer/0
              1.8 ms/s       4.4        Interrupt      [17] ohci_hcd:usb3
              1.6 ms/s       3.2        Timer          tick_sched_timer
              1.4 ms/s      24.8        Process        powertop
              1.0 ms/s      0.00        Interrupt      [1] timer(softirq)
              1.0 ms/s      0.00        kWork          do_dbs_timer
```I would appreciate any help in identifying things I can get rid of to improve my battery life...

---

### Post by chadk5utc on 2012-12-04
You may also look into CPU throttling. Heres a link with lots more that maybe helpful. 
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

Chad

---

### Post by howefield on 2012-12-04
Thread moved to the "*Apple Users*" forum.

---

### Post by 2F4U on 2012-12-04
Since you are already using powertop, are there any suggestions from this tool? If yes, it may be worth posting them.

---

