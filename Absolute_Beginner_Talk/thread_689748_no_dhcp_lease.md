---
title: "no dhcp lease"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by bsharp on 2008-02-06
I just got a new laptop after my old one crapped out on me

Anyway, its a compaq presario f700, with a atheros ar5007eg wireless card along with a wired ethernet as well. I got the drivers installed no problem with ndiswrapper (I am running 64 bit so no madwifi for me :( ) my iwconfig is this:
```
lo        no wireless extensions.
eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

but when I try to connect it with my AP, i am not recieving a DHCP lease. I don't know if this is a problem with my card or the AP, but something isn't working.

---

### Post by freddyp on 2008-02-06
Do you have any MAC filtering turned on?

---

### Post by bsharp on 2008-02-06
all filters are off, i even reset my router to the factory settings, but still nothing.  it is an old router btw, so when i get the chance i will try it with a different one

---

