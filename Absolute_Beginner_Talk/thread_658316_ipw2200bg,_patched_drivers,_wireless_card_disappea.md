---
title: "ipw2200bg, patched drivers, wireless card disappeared?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by rayraymo on 2008-01-04
I'm currently trying to turn my Xubuntu install into a security testing OS, (Previously using BackTrack but I couldn't get it to install on this laptop.). I'm using a intel 2200BG , and am trying to set it up to show people how easy it is to crack WEP wireless networks.

Basically I patched the driver using this guide- [http://aircrack-ng.org/doku.php?id=ipw2200#ipw2200](http://aircrack-ng.org/doku.php?id=ipw2200#ipw2200)

Then the wireless in KNetworkManager just disappeared. 

I presumed that-
sudo rmmod ipw2200

Would renable the card but it gives me the error-
ERROR: Module ipw2200 does not exist in /proc/modules

Not quite sure where I've gone wrong.

Any help would be greatly appreciated.

Thanks, Raymo

---

### Post by rayraymo on 2008-01-04
update-

when i run, dmesg | grep ieee, i get-

rayraymo@ubuntu:~/Wireless/ieee80211-1.2.18$ dmesg | grep ieee
[   64.664000] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   64.664000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   64.664000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   64.664000] ipw2200: Unknown symbol ieee80211_txb_free
[   64.664000] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   64.664000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   64.664000] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   64.664000] ipw2200: Unknown symbol ieee80211_set_geo
[   64.664000] ipw2200: Unknown symbol ieee80211_rx
[   64.668000] ipw2200: Unknown symbol ieee80211_channel_to_index
[   64.668000] ipw2200: Unknown symbol ieee80211_rx_mgt
[   64.668000] ipw2200: Unknown symbol ieee80211_get_geo
[   64.668000] ipw2200: Unknown symbol free_ieee80211
[   64.668000] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   64.668000] ipw2200: Unknown symbol alloc_ieee80211

And so I think the ieee part isn't installed properly. Any ideas?

---

### Post by LookTJ on 2008-01-04
if you did:
> sudo rmmod ipw2200

That disabled the module. To enable the ipw2200 module, do:

> sudo modprobe ipw2200

---

### Post by rayraymo on 2008-01-04
Thanks for the reply, how ever that didn't work either it gave me the error-

WARNIng: Error inserting ieee80211 (/lib/modules/2.6.20-15-generic/net/ieee80211/iee80211.ko):Unkown symbol in module, or unkown parameter (see dmesg)
FTAL: Error inserting ipw2200 etc etc etc

Anymore ideas? I'm thinking it somehow is because I'm using Xubuntu n the guide is for Ubuntu.

---

### Post by LookTJ on 2008-01-04
> **rayraymo said:**
> Thanks for the reply, how ever that didn't work either it gave me the error-

WARNIng: Error inserting ieee80211 (/lib/modules/2.6.20-15-generic/net/ieee80211/iee80211.ko):Unkown symbol in module, or unkown parameter (see dmesg)
FTAL: Error inserting ipw2200 etc etc etc

Anymore ideas? I'm thinking it somehow is because I'm using Xubuntu n the guide is for Ubuntu.Hmm, have you enable the ieee module first?
> sudo modprobe ieee80211

after you do that, try enabling the ipw2200 drivers, then do:
> dmesg | tail
to see what's up when you still get errors.

---

### Post by epb on 2008-03-16
I have a similar problem.. by trying

```
dmesg | tail
```

i get

```
[  656.772000] Kill switch must be turned off for wireless networking to work.
[  656.772000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[ 1761.288000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[ 1778.080000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
[ 1778.080000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 1778.080000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[ 1778.080000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 1778.212000] ipw2200: Radio Frequency Kill Switch is On:
[ 1778.212000] Kill switch must be turned off for wireless networking to work.
[ 1778.216000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
```

Something's missing? Or need to be done? There's a little LED which should be on when the card is working, but it is turned off and I cannot access my wireless network

---

