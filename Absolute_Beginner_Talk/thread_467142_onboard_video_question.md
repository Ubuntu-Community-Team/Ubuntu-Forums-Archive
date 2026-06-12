---
title: "onboard video question"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-06-07
i was trying to figure out if 1280*1024 was the highest resolution that onboard video would support i have an intel 
chipset driver 945 and i edited the etc.config file to only show 1440*990 and the highest it gets is 1280*1024

you guys rock on here and the irc channel

---

### Post by NilsE on 2007-06-07
> **reston5 said:**
> i was trying to figure out if 1280*1024 was the highest resolution that onboard video would support i have an intel 
chipset driver 945 and i edited the etc.config file to only show 1440*990 and the highest it gets is 1280*1024

you guys rock on here and the irc channel
With the Intel chip you need to use 915resolution or replace the default i810 video driver with the Intel driver.

I would start with the Intel driver.  Go into Synaptic and search for Intel and you will find it.  Select it for install and it will prompt you to uninstall the i810 driver. 

If you need to go back then find the i810 driver and select it and it will prompt you to uninstall the Intel driver. 

If you want to try 915resoution look here [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

I am assuming you are on 7.04

---

