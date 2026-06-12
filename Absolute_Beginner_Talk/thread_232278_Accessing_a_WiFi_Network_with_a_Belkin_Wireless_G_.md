---
title: "Accessing a WiFi Network with a Belkin Wireless G Notebook Network Card - F5D7010"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Village on 2006-08-08
I've been trying to get my Laptop to access my wireless network (as its Summer I want to go and sit outside in the garden). I've recently got into Ubuntu (so I'm new to all of this) and I have installed 6.06 on my P3 1ghz Laptop. 

I've been able to get internet access though a wired connection plugged into the back of my laptop and my wireless router. I have a Belkin Wireless G Notebook Network Card – F5D7010. 

I've installed NdisWrapper and tried (what I think is) the right driver (no. 24 [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")), occasionally I see the wireless card pop up on the Network Settings (System>Administration>Networking) but its not always there. and then sometimes to add to my problems the laptop crashes.

According to my Device Manager (System>Administration>Device Manager) my WiFi card is there. But it doesn't pop up on the Networking settings? If I could get it to remain on there then I might stand some chance of sitting in my garden before summer's over.

Any help much appreciated as I've been playing around with this for a couple of weeks now.

Thanks

Village

---

### Post by jeff_ on 2006-08-08
What happened after you installed ndiswrapper? What output do you get if you go to a terminal and type 'ndiswrapper -l'? What output do you get from typing 'iwconfig' and 'ifconfig' in a terminal?

When your wifi card does popup under network settings do you have wireless access?

---

### Post by Village on 2006-08-08
I've seemed to get it working now. Basically what I did was install NdisWrapper (both Ndisgtk and ndiswrapper-utils from the synaptic package manager and then run the driver mentioned below though it. After playing around with it I restarted it a couple of times and then put my wifi card into my system and after setting the network settings to use my card it seems to be working. I'm not to sure how though, but I'm not complaining.

Village

---

### Post by jeff_ on 2006-08-08
That's good news, wish you knew what got it working though. Welcome to linux and enjoy your garden!

---

