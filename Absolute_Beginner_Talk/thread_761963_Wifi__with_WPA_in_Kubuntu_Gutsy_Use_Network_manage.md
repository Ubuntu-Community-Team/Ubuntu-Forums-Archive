---
title: "Wifi  with WPA in Kubuntu Gutsy: Use Network manager!"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by kle on 2008-04-21
When you right-click the ikon for Network Manager, you are supposed to see all available Networks, also those that are password protected, unless they are hidden (not broadcast). 

If the one you want is there, click it. If connection fails, you may have to configure it. I have been unable to do so otherwise than by picking "connect to other wireless network". There I can specify my prefs. _including_ WPA.

If you don't see the option "connect to other wireless network", or if the networks you see are funny, you will have to clean up the Network Manager's interfaces file, like this. In console type
   
[I]kdesudo kate /etc/network/interfaces
[/I]
Now remove all but the two lines: 

[I]auto lo
iface lo inet loopback
[/I]

Save the file. Reboot. Now you have a clean slate, as it were, and can set your connection prefs. NB there is no point in trying "manual configuration", because it does not allow WPA.

---

### Post by kle on 2008-04-22
I forgot to add this about "hidden" (non-broadcasted) networks: 

If you have a hidden network, you will not see it when you right-click the Network Manager icon. You can tell NW it is there, though, with the "connect to other network" option. Unfortunately, you may have to do this every time you log in (which is a nuisance, admittedly). 

Also: In Kubuntu, at least, using WIFI triggers a demand for your a  password which is stored in Kwallet. 

See FAQs here:
[https://answers.launchpad.net/ubuntu/gutsy/+source/knetworkmanager/+questions](https://answers.launchpad.net/ubuntu/gutsy/+source/knetworkmanager/+questions)

---

