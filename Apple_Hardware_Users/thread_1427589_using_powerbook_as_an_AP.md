---
title: "using powerbook as an AP?"
date: 2010-03-11
forum: Apple Hardware Users
---

### Post by egorFiNE on 2010-03-11
Hi! 

I've just installed Ubuntu 10 alpha on a 15" powerbook of one of the last models (1.5ghz, etc). I updated all packages and Airport card works perfectly in client mode - I can connect to other networks, can create ad hoc networks, etc. 

However, I am trying to make this notebook an access point at home and seems like I cannot make this card go into master mode: 

```

$ sudo iwconfig  wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

```

I've googled the net and the clues are that Broadcom 4306 should work as AP. Even the "iw" tool says so: 

```

$ sudo iw phy0 info
...
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * WDS
		 * monitor
		 * mesh point
...

```

Plz help: how do I enable master mode for this card in powerbook?

PS: In case you need additional info about the machine - it's connected via ethernet at 93.73.236.110, l/p helpme, **port 22222**, sudo enabled. Please don't hurt :)

---

### Post by linuxopjemac on 2010-03-12
> I few weeks ago a tried to configure my PC as a wireless router so other devices can get connected throught my PC, i think it's kind of what you want. I have a Broadcom wireless card too.

If you set your card in Ad-Hoc mode it will work. It did with me.
[http://old.nabble.com/Broadcom-drivers-to-enable-master-mode-td23235319.html](http://old.nabble.com/Broadcom-drivers-to-enable-master-mode-td23235319.html)

Why do you use such a nice computer as an AP? Buy a cheapo router and you are done.

---

### Post by egorFiNE on 2010-03-12
> **linuxopjemac said:**
> [http://old.nabble.com/Broadcom-drivers-to-enable-master-mode-td23235319.html](http://old.nabble.com/Broadcom-drivers-to-enable-master-mode-td23235319.html)

Yeah, ad hoc mode works well. But I am looking into master. 

> **linuxopjemac said:**
> Why do you use such a nice computer as an AP? Buy a cheapo router and you are done.

:-) It's half dead. Not usable as a desktop anymore. So I decided to make it a nice router/iTunes server/NAS/Multimedia player. A perfect retirement for a Powerbook.

---

### Post by linuxopjemac on 2010-03-12
I found some info here:
[http://acx100.erley.org/acx/nl80211_master_mode.html](http://acx100.erley.org/acx/nl80211_master_mode.html)

and slow transfer rate problem 
[http://lists.shmoo.com/pipermail/hostap/2008-November/018800.html](http://lists.shmoo.com/pipermail/hostap/2008-November/018800.html)

hostapd:
[http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

---

### Post by egorFiNE on 2010-03-13
Solved. I had to properly configure hostapd.conf and run it. It will make the wlan0 into mode master and take care of the AP. 

```

driver=nl80211
interface=wlan0
hw_mode=g
channel=5
ssid=NETWORK_NAME
wpa=1
wpa_pairwise=TKIP
wpa_passphrase=PASSWORD

```

---

