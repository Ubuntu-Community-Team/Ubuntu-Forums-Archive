---
title: "How do I know it's working?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Mallette on 2007-06-15
I'll keep it simple:
1. How do I verify my wireless is working?
2. How do I view available wireless networks?

When I originally booted the Ubuntu CD on my company Dell Latitude laptop, it found the network and came right up.  However, I've installed it on an emachines laptop and I cannot see anything to verify either that the wireless is working or what is available.  

Can't learn much else until I can access help and such...

Dave

---

### Post by Rocket2DMn on 2007-06-15
If the wireless signal you're trying to connect to has an internet connection, you should be able to view webpages if you're connected.  If you DON'T see webpages, you probably aren't connected

You can view wireless networks by using the network manager tray icon by the clock

---

### Post by overdrank on 2007-06-15
> **Mallette said:**
> I'll keep it simple:
1. How do I verify my wireless is working?
2. How do I view available wireless networks?

When I originally booted the Ubuntu CD on my company Dell Latitude laptop, it found the network and came right up.  However, I've installed it on an emachines laptop and I cannot see anything to verify either that the wireless is working or what is available.  

Can't learn much else until I can access help and such...

Dave

Hi and welcome, you can start by going to system, admin, networking and see it your wireless it recognized. If it is not the use the command in the terminal ( located under applications, accessories, terminal) lspci and post here and maybe we can help you. :KS

---

### Post by Mallette on 2007-06-16
Thanks for the input.  I am on it today...

Since I don't have access I cannot supply the whole response, but it appears to confirm recoginition.  It is a Broadcom BCM4306.  Ethernet is a BCM4401 rev. 01.  

Network settings shows "roaming enabled"  but I do not see any networks avialable.  I used the connect dialog to enter my ssid and pw and it ground awhile, but did not connect.  I used the WPA Personal setting under the assumption that is is correct.  "Assumption" in that this is not terminology I am familiar with.  My net is WPA-PSK with AES encryption.  

I knote the ALi M5451 audio device also appears to be installed but I have no sound.  It is not muted or anything simple.  

Thanks again for the help and let me know if there is more I can provide.

Dave

PS - I tried a manual cofig but there is nothing available there but WEP...which isn't going to work.  I know the machine supports current standards as I've used it under Windoze.

---

