---
title: "My wireless card has gone"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by lebski88 on 2006-09-30
Hello everyone,

I've been trying to get wireless to work with Ubuntu.

I installed ndiswrapper and I've been trying to get my .inf registered with it. Unfortunately it tells me that my .inf is an invalid driver. I know the driver has worked with ndiswrapper before as I had it working on SuSE.

However I just checked the networking settings and my wireless card  no longer shows up. Previously it was mounted as wlan0 but now it's  missing from the dialog. Ifconfig and iwconfig don't show it either. According to the help file in the network settings I should be able to add a new connection but there is no button for that, only; properties, activate and deactivate. Before I started messing with ndiswrapper the card was there.

My card shows up in device manager so I know that linux can see it.

I'm not sure if this is relavent but following the ubuntu ndiswrapper instructions I ran:

rvmod acx

I'm not sure if ndiswrapper is failing to work because my wireless card is missing or whether that is unconnected. 

Does anyone have any ideas where I should go from here?

---

### Post by lebski88 on 2006-09-30
Err scrap that everyone I was missing the .sys file. That will teach me to try and setup linux at 4:30 in the morning!

Sorry for wasting everyone's time.

Thanks,

Ben

---

