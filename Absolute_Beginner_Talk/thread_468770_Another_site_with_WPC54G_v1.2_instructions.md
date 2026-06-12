---
title: "Another site with WPC54G v1.2 instructions?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by pjbm on 2007-06-09
hi there,

I am a real newby with my first foray into a non-windows system! I have an old dell and a Linksys wireless card model WPC54G v1.2 and I have found a page with instructions on how to get it going here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

-> [http://bcm43xx.spugna.org/index.php?topic=29.0](http://bcm43xx.spugna.org/index.php?topic=29.0)

But the link is to a site that is down. Does anyone have the instructions by any chance somewhere else as I have an hour up my sleeve at the moment to have a fiddle at getting it going.

Any help/advice would be appreciated!

Thanks
P

---

### Post by shearn89 on 2007-06-09
to get it set up you'll need to install ndiswrapper first. I'll have a quick look for the how-to i followed (i have the WPC54GX, basically the same card)


The easiest way to install ndiswrapper is to go System -> Administration -> Synaptic, then search for "ndis", right-click on ndiswrapper (the one that looks like the main one), and go "install". Then hit apply - it will download and install. You can do the same for wpa_supplicant (see link below).

here is a how to if you use WPA security: 
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

installation instructions for ndiswrapper (you need this as the linksys cards don't have native linux drivers. ndiswrapper "wraps" the windows ones.)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)
you can ignore most of it, just skip to the last bit where it says
```
ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```
assuming you've already set up wpa_supplicant.

if you have any trouble, i'll do my best to help... It took me a while of just messing around with the wpa_supplicant.config file to get mine going, so you may need some patience.

The easiest way to install ndiswrapper is to go System -> Administration -> Synaptic, then search for "ndis", right-click on ndiswrapper (the one that looks like the main one), and go "install". Then hit apply - it will download and install. You can do the same for wpa_supplicant.

---

### Post by pjbm on 2007-06-09
Thanks very much.. I am going to have a play!

---

