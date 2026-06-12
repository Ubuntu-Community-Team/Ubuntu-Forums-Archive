---
title: "network interfaces"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by tekwarren on 2006-02-13
Ok so i was trying to "optimize" my startup/shutdown time following a how to here in the forum. Anyway I started making changes in my /etc/network/interfaces and I think I foo'd something up. I must have some wrong changes and so tried to change it back. My eth0 still works but my wlan0 is not showing up now as I think i removed it or changed something with that. It does boot faster now...alot faster but I want to re-add the wlan. I am just wondering if someone can post their interfaces file or tell me what it should say to include the wlan. I had it all working previously with ndiswrapper (broadcomm) so I'm assuming I just need to re-enter into the file? It also does not show up in the administration-networking anymore. Please advice!


Thanks

---

### Post by TrendyDark on 2006-02-13
it's not showing up in the network interface list? maybe try seeing if the ndiswrapper module is loading on boot up?

```
sudo gedit /etc/modules
```

---

### Post by tekwarren on 2006-02-14
these are the only things it shows loading:

lp
mousedev
psmouse
sbp2
sr_mod


The changes I made where to the services that startup/shutdown I originally disabled hotplug and hotplug-net but re-enabled them both. I also tried making changes to the /etc/network/interfaces so that the devices loaded quicker...i think the how to said something about commenting the section that does the mapping...I'm not sure (newb) but I thougth I restored everything back to normal. My boot up time takes forever again unless I control+c  the network loads. This morning I can't connect with my eth0 but it is there and I can access it via the administration-networking. I can use the wireless if I do a sudo modprobe wlan0 but it won't show up under networking unless I do that. Do I need to somehow reload/readd something so its automatically "detected" as a device durring startup? Its painefully slow at boot but i guess if it has to be that way to keep both wireless and wired options available I will deal with it.

Thanks!

---

