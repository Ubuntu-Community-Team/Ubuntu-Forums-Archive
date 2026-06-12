---
title: "Can't get wireless working"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2006-08-17
Hi all, first let me say this is a fantastic package, and it's finally motivated me to switch from Windows.

I've installed 6.06 on my Thinkpad T60.  I've followed a number of posts here and at [http://www.linux-on-laptops.com/ibm.html](http://www.linux-on-laptops.com/ibm.html) trying to get everything up to speed, and the one thing I can't get working is the wireless.

Running iwconfig gives me this:

eth1 unassosciated ESSID:"mywireless"
     mode: managed Frequency=nan  Access Point: Not-Associated

and more which should be inconsequential.
Whenever I try to turn the wireless on the little activity light on the laptop goes NUTS, and doesn't stop until I flip the switch to turn it off.

Under Network Settings, the wireless connection shows up as eth1 and says it's active, and if I select eth1 as the default gateway device, and go to properties I can see the various networks around me.  If I chose one and click OK, it takes a full 2 minutes to exit the "Activating interface "eth1", then my system monitor shows a lot of activity and the light continues to go nuts - it just doesn't work.

It seems like I'm close though...
Any help would be much appreciated

---

### Post by oss_monkey on 2006-08-17
Welcome to Ubuntu! Let me be the first to congratulate you for the switch. :)

Anyway, to your problem: I've encountered that error when I tried installing the wireless. I think your card isn't installed yet. From my experience, Ubuntu assigns "eth" to ethernet devices. In my case, it used "wlan0" for my wireless device. Maybe it's the same with you.

I used a Linksys PCMCIA card, so I followed this thread for installation. A bit of tweaking should help you install the card first and foremost. [Wireless-G Setup]("http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101")

Second, I recommend using [WiFi-Radar]("http://wifi-radar.systemimager.org/") for your WiFi needs. Stay away from gtk-wifi. It only caused me trouble.

Good luck!

---

### Post by PriceChild on 2006-08-17
No... your card is all installed fine as good as my guess is.

I've always hated wifi-radar... i REALLY REALLY reccommend installing the gnome-network-manager package, which gives you a very nice icon next to your clock and works beautifully.

Personally, i used the standard network manager to enter my hub's ESSID and passwords, but i use gnome-network-manager when roaming and for my ethernet cards.

---

