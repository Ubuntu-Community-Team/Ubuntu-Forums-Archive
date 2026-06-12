---
title: "stuck - linksys wpc54g pcmcia"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by tommyg on 2005-12-24
well, things were going smoothly as I followed all the instuctions for getting the wireless card working, but I've hit a roadblock.  the ndiswrapper has sucessfully installed the Windows driver:
```

ndiswrapper -l
Installed ndis drivers:
lsbcmnds        driver present, hardware present
```

and modprobe does its job on boot and gives me a wlan0 interface. iwconfig output looks like this:

```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

regardless of my WEP settings (or lack thereof) the card will not transmit or receive both with and without DHCP enabled (yes... my DHCP server is running).  if I set a static IPv4 address it will list it in ifconfig, but still won't communicate with the rest of the LAN.

this is a Linksys WPC54G card using both the latest Windows XP drivers from the linksys website and the driver from the CD.  and the machine is a Gateway 400SD4 notebook.

i'm gonna keep pluging away... if anyone has any ideas please let me know!

---

### Post by waldorf on 2005-12-24
I found this thread very helpful especially the post from ahave2005

[http://ubuntuforums.org/showthread.php?t=99490](http://ubuntuforums.org/showthread.php?t=99490)

---

