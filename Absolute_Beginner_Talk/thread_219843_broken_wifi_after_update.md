---
title: "broken wifi after update"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by timofthec on 2006-07-20
OK - so after much wrangling I've finally managed to get me belkin wireless card - broadcom chip and all - working and can access the internet with no probs.

However, I recently updated the kernel (hehe - i know techno speak now ;) ) from 2.6.15-23-386 to 2.6.15-26-386 and now I cannot get on to the internet.

As far as I can tell, the drivers are all still there and active and wifi radar can see my router and ssid.  The only difference that I can see is that in the original kernel under wifi radar it tells me that its connected under IP() whilst in the updated kernel wifi radar says its not connected to an IP.  I've attempted to tell wifi radar to connect to the router but after a scan to obtain an IP address its tell me that it cannot connect.

Looking under networking it also tells me that the device is there and that the wlan0 is active.

Anyone got any ideas please?

---

### Post by OU812 on 2006-07-20
Check this out.

[http://ubuntuforums.org/showthread.php?t=213420](http://ubuntuforums.org/showthread.php?t=213420)

john

---

### Post by timofthec on 2006-07-20
thanks for that john, I think we scared it in to working though:p 

I looked at the thread and made some notes and then I installed the wireless assistant - just in case I needed it.

I rebooted into the latest version and the wireless network is now up and running - and all I did was stare at it in a troubled manner.  Its strange cus I've been unable to get onto the internet with the new kernel since I updated two days ago.

Not sure whether I was just being impatient or whether installing the wireless assistant did something but its up at the mo :D 

Thanks again

---

