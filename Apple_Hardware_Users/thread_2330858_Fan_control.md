---
title: "Fan control"
date: 2016-07-15
forum: Apple Hardware Users
---

### Post by zenbat on 2016-07-15
Hi, I installed 14.04 back around October 2015 on my mid-2009 iMac and noticed fans were pretty loud. At the time, I found some tips online about quieting them; they'd always run loud during boot, but quickly quiet down.

I wiped the Ubuntu install the other day and tried 16.04. Initially the fans were quiet, but after a bit of time the fans became louder and louder. I've tried the macfanctld, which is what I think I did before, but no change.

I've installed Psensor and noticed that the CPU and ODD fans are stable, but the HDD fans slowly increases at a perfectly steady rate over time. I thought perhaps temps were increasing gradually, leading to this increase in fan speed, but in actuality all the temp readings are table and most show a couple degrees lower than the max they hit during the current uptime. Very strange!

Any idea why the HDD fan slowly increases speed and how to get it under control?

Thanks!

---

### Post by awjrichards on 2016-08-20
What does your /etc/macfanctl.conf look like? I found the default settings to be overly aggressive for cooling my MacBook Air 6,2.

---

