---
title: "wireless contact?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by epo on 2006-12-27
Hi,

I'm running Ubunto Desktop 6.10 for a few hours and I'm liking it already. One thing that I'm unable to accomplish it to get the wireless connection running. Ubuntu recognizes the ZyAir G-220 USB stick, the wlan0 is active, the wep-key is entered, but ... I'm unable to surf the internet. Pinging a known ip-address doesn't work either. Maybe I forgot to switch on something else?  Please give me a hint.

Thanks,
Erwin

---

### Post by gustolove on 2006-12-27
well, if you don't mind using the command line u can do this:
```

iwconfig [adaptername] essid [SSID-nameofnetwork] enc [WEP-encryption]

```
Replace everything in [] with the correct information... what that does is just configure the adapter with the ssid and the encryption key... also u can type:
```

iwconfig [adaptername]

```

to get a detailed list of wireless information such as signal strength and such

---

### Post by epo on 2006-12-27
Thanks,

after typing the two commands I get:

iwconfig wlan0
wlan0     802.11b/g NIC  ESSID:"EmmaNet"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:13:49:44:FE:AE
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=64/92  Signal level=35/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This seems ok, but after starting Firefox, I can not get a connection. Do I need to configure more?

Thanks,
Erwin

---

### Post by epo on 2006-12-27
It seems to work after a few minutes. Strange, but I'm happy. 

Thanks,
Erwin

---

