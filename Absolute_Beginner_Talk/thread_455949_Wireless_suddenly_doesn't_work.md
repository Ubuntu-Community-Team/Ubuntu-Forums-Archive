---
title: "Wireless suddenly doesn't work"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by rootie on 2007-05-27
I have been using Feisty for some time now (a little more than a week, to be exact =P) and I never had any problems with the wireless from the beginning. Now however, after a two-day outing, the wireless just stopped working. It still works on a WinXP box. I don't really know what could have messed my configuration up, as I was unable to find any hotspots during my trip. The worst thing that happened was OpenOffice choking on a Office07-formatted ppt file.

(I'm currently connected via wired lan.)

Thanks for any help. :D

---

### Post by omkarwagh on 2007-05-27
did you use your wireless on the trip? if so did you need static ips for that place?

i once spent two days trying to figure out what was wrong and i eventually found id forgotten to change the ip settings to dynamic again.

also since im a beginner to ubuntu i don think i can help you out technically but i hope this helps.

---

### Post by rootie on 2007-05-27
Hi omkarwag, no, I wasn't able to connect to the internet at all then. I checked my configuration anyway, and I'm on roaming mode? Not sure if that's the configuration that could've been changed. =P

I've rebooted the laptop and the modem+router a few times and it's still not working, so I'm convinced it's a setting somewhere... True test will be when I get to the office later. =P

---

### Post by ugm6hr on 2007-05-27
> **rootie said:**
> Hi omkarwag, no, I wasn't able to connect to the internet at all then. I checked my configuration anyway, and I'm on roaming mode? Not sure if that's the configuration that could've been changed. =P

I've rebooted the laptop and the modem+router a few times and it's still not working, so I'm convinced it's a setting somewhere... True test will be when I get to the office later. =P

If you use Network Manager (the default wireless roaming wizard for Ubuntu, then enable roaming mode should be on.  You should have a nm-applet icon (4 vertical grey bars) somewhere on the taskbar panel (usually top-right) that says "No connection" or something like that when your cursor passes over it.  If so - right-click and enable networking and wireless, then left-click and select a network.  If not - type *nm-applet* in Terminal to bring it back, and try again.

---

### Post by rootie on 2007-05-27
Umm :D I may or may not have solved the problem. You see, my laptop has a little bulb that lights up when the wifi's enabled. It doesn't light up with Ubuntu. I always thought that "Enable Networking" and "Enable Wireless" (right click that nm-applet icon) meant that the wireless card's on, but I tried to solve my problem rather radically by turning the wireless card on the old fashioned way (pressing the button). I guess I somehow clicked it during my trip? Really sorry if my problem sounds stupid now. I'll check to see if it's plugged in before I ask. XD

Thanks omkarwag and ugm6hr for the help :D

[I'll come bug you guys later if it doesn't work from home =P]

---

