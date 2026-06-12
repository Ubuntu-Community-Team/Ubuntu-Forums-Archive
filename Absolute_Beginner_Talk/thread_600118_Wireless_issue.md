---
title: "Wireless issue"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by doomgazer on 2007-11-01
I'm a newbie to ubuntu and rather new to the linux world in general, so please bare with me.

I've got a Dell Precision M70 with an Intel Pro/Wireless 2200BG wireless adapter. I'm having a really strange wireless performance problem, but only on my home wireless AP.

My AP is a Linksys WAP54G running DD-WRT firmware v23. It is configured to hide the SSID and WPA-PSK using TKIP. When I connect to it, my download speeds are absolutely terrible (50-80kbit), whereas my upload speeds seem completely unaffected (around 700kbit). If I connect to my neighbor's AP who uses the same ISP, but has no encryption on it, I get full speeds.

Initially I thought it was something to do with the WPA, but I disabled everything and set it back to an open and unsecured wireless system with SSID broadcast on - no avail, still getting terrible download speeds.

I run a Windows 2003 server for DNS and DHCP, but I don't think that is the issue, as I tried my ISP DNS servers and it didn't change the situation. Is there some kind of compatibility issue with the DD-WRT firmwares and Ubuntu?

I should also point out that under XP, this laptop performed fine on the wireless end of things on this AP, and none of my other wireless PCs are having issues.

Any help will be greatly appreciated. Thanks!

---

### Post by ajmorris on 2007-11-02
hi,
This is a bug with quite a few Dell wireless cards. The solution is ndiswrapper with the windows drivers. I actually use these windows drivers over ndiswrapper with my 1390 mini pc card. The 1370 is in your model i believe, however both run from a broadcom 4311, so my ndiswrapper drivers will work for you too :)

The problem is, i cant remember where i got the Drivers from. Search in google for broadcom 4311 linux wireless drivers, or something, or Dell Precision M70 wireless drivers :) i'll keep looking around for them though too

---

### Post by doomgazer on 2007-11-02
Nope - it's not a Dell Wireless card, it's an Intel Centrino Pro/Wireless 2200BG.

Again, the wireless performs just dandy on my neighbor's wireless network, but when I connect to mine, the download goes to pot on me - upload seems unaffected. A speedtest from my ISP's speed test, shows around 50-90kbit download (that's kbit, like dialup speeds) and 700kbit on the upload. The other wireless machines on my network see around 4-5mbit and 700kbit.

---

### Post by doomgazer on 2007-11-04
Solved the problem - wasn't anything to do with my wireless - had the same issue wired in. Seems it was related to a Cisco 871 router I was using. Replaced it with a Netgear WPN824 and all is working wonderful again.

Not sure if it's a configuration problem on the Cisco or what, but that was the problem.

---

