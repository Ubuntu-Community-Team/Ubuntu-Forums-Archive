---
title: "Wireless works when manually inputting settings"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2008-03-08
Hello, I have a slight problem with NetworkManager, I can connect to my wireless network by manually inputting my SSID, WEP Key and selecting DHCP, but i use 2 other WLAN's also. NetworkManager shows as "no network connection" but I am connecting to my WLAN now. I first thought it was to do with ndiswrapper but i have just reinstalled ubuntu and it works straight away, when manually inputting settings. 

Is there a resolution for this problem?

Thankyou

---

### Post by spiderbatdad on 2008-03-08
I'm thinking maybe the different wlans are writing and/or erasing (existing) nameservers in /etc/resolve.conf 

You might compare what is written there before and after enabling the several wlan's. This may be a bug.

---

### Post by MikeJ112 on 2008-03-09
Possibly no quick fix for this then! Its nothing too major, I can still connect to the internet on my own WLAN which is the main purpose of my linux box.

---

### Post by lswest on 2008-03-09
or you could use something like kwifimanager where you can input the information and store it (basically it stores the info then runs the commands in the terminal without you having to input everything)

---

### Post by MikeJ112 on 2008-03-09
I did install KWifiManager last night, but when I scan for networks it only shows my own. I booted into XP last night (im dual-booting) and it shows 5 networks in range?

---

### Post by lswest on 2008-03-09
yeah...the scan function doesn't work too well, i use the configuration editor Settings-->Preferences then give in your password, and add in what you need to the configs.  if it doesn't open you'll need to install kde-base, which will install a LOT of other programs, but you can just remove the entries in your menus, or give WICD a try

---

### Post by MikeJ112 on 2008-03-10
Something else weird has just happened, i have disable networking but it connected to another unsecured wireless network earlier without me even knowing. Would it be easier to buy a new wireless adaptor which is supported better by linux?

---

### Post by lswest on 2008-03-12
which network manager are you using?  if you want, you could drop network managers completely and input the commands manually (or, you can follow [my how-to on aliasing]("http://ubuntuforums.org/showthread.php?t=721533") and set up aliases for connecting to networks you know).

---

