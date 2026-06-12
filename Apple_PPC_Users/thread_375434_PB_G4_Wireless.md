---
title: "PB G4 Wireless"
date: 2007-03-03
forum: Apple PPC Users
---

### Post by monkeytwotwo on 2007-03-03
I just unstalled 6.10 over firewire and everything works fine.

I start up Networking from the Administration menu and activate the recognized bcm43xx card. But somehow nothing happens. iwconfig gives me this:

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If I enter the ESSID in Networking and save it, iwconfig gives me ESSID:""
If I start wifi-radar it tells me: eth1 Interface doesn't support scanning : No such device.

Could it be that 6.10 didn't recognize my wireless card right?
Or what could I try to fix this?

---

### Post by stmiller on 2007-03-03
You have to extract the firmware from the Apple wireless driver for this card to work in Linux. Search the forum for broadcom.

---

