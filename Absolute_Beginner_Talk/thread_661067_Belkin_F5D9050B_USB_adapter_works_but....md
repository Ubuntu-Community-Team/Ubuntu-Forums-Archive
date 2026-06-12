---
title: "Belkin F5D9050B USB adapter works but..."
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by desertphotog on 2008-01-07
I cannot force it to connect to MY own network. It will always default to a neighbor's signal. When I click "Connect to Other Wireless Network", the icon just spins and won't find anything! Then, it won't re-connect with anything until I re-boot. How can I make the so called "Network Manager" change the order of the connections? BTW, the machine is dual boot with XP and with "their" network manager, I can pick-and-choose hotspots VERY easily. I want to show my friends this Unbutu is as good as Windoze but I still have a lot to learn. Setting up the dual boot was a piece of cake compared to the WIFI !

---

### Post by dfault312 on 2008-01-09
how far is your wireless router from your linux machine? (im guessing its pretty close if your xp machine doesnt have a problem connecting) when you boot windows, try going into your wireless router's settings (should be 192.168.0.1, but it might be different) and make sure that your router is set up to broadcast itself. try reseting your router to defaults if you havent made any important changes to the settings. it may be a security setting that you have enabled that is interfering with linux's ability to discover your router.

---

### Post by dfault312 on 2008-01-09
also, my belkin router is at 192.168.2.1 by default, so you could try that if 192.168.0.1/2 doesnt work. i dont really know much about how IP addresses are assigned.

---

