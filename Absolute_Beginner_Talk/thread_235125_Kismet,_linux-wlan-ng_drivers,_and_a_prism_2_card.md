---
title: "Kismet, linux-wlan-ng drivers, and a prism 2 card"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by nerdtalker on 2006-08-12
Well, after more than an hour of trying, I've only managed to get linux-wlan-ng installed, and kismet installed by using apt-get, but not working yet.

apt-get reports that linux-wlan-ng is installed, but I'm pretty certain that whatever old wireless driver was installed is still installed, and I don't know how to remove/disable that old driver. 

I've edited kismet.conf correctly, namely the setid and source lines:
> # to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wlanng,eth2,Prism

But running sudo kismet gives me:
> Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Prism): Enabling monitor mode for wlanng source interface eth2 channel 6...
Source 0 (Prism): Opening wlanng source interface eth2...
FATAL: pcap reported netlink type 1 (EN10MB) for eth2.  This probably means you're not in RFMON mode or your drivers are reporting a bad value.  Make sure you have the correct drivers and that entering monitor mode succeeded.


So I'm pretty certain that wlan-ng isn't setting mode monitor, or just isn't installed.

Could anybody tell me how to properly setup my wireless interface? I use wlancfg, right? The card is a Prism 2 SenaoNL-2511CD Plus EXT2 (pretty nice 200mW card). :cool:

---

### Post by srf21c on 2006-10-16
I have the same card as you and was able to get Kismet working using the default orinoco_cs driver/module

This kismet.conf source line works with the orinoco driver

```
source=orinoco,eth1,HermesI
```

Since then, I've "upgraded" to the hostap driver by installing the hostap-utils package

```
sudo aptitude install hostap-utils
```

I believe installing the hostap-utils package automatically blacklists the orinico_cs module, thus allowing the hostap_cs module to load.  If not, you can always manually blacklist the orinoco_cs module by adding this line to /etc/modprobe.d/blacklist

```
blacklist orinoco_cs
```

My eventual goal is to get the latest wlan-g driver compiled with the appropriate patch so I can do packet injection and other cool stuff.

---

### Post by yeehawjared on 2006-10-24
I have the same card -- don't you mean that you want HOSTAP drivers installed for injection?

I use Back|Track a lot and successfully inject with hostap drivers.  In fact, I never switch to wlanng.  I can't seem to patch hostap on my ubuntu box to save my life... I'll keep this thread updated with my progress.

---

