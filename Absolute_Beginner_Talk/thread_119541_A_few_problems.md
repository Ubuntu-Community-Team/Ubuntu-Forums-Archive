---
title: "A few problems"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by FBI on 2006-01-19
This is my first time using any Linux distribution, and, after installing, I've come up with some problems:

1) The HAL (harware abstraction layer?) seems to be having problems. When I log in, an error message pops up, saying "Error: failure to initialize HAL."

2) My printer registers with the system, but the printer properties always say that the port in question is busy.

3) I've installed ndiswrapper and gotten my wireless card (Linksys WMP54GSa) to register, but the card can't find the sole wireless network in the area, one that Windows can always find. iwconfig displays this:
```

wlan0        IEEE 802.11g ESSID:off/away
             Mode: Managed Frequency:2.412 GHz Access Point:00:00:00:00:00:00
             Bit Rate:54 Mb/s Tx-Power:25 dBm
             RTS thr:2347 B Fragment thr: 2346 B
             Power Management:off
             Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
             Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
             Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```
These all seem interrelated. Am I missing something?

---

