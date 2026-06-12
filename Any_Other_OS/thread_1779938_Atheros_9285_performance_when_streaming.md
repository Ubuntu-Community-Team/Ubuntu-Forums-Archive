---
title: "Atheros 9285 performance when streaming"
date: 2011-06-11
forum: Any Other OS
---

### Post by HydroDiOxide on 2011-06-11
I'v got some problems in Ubuntu 10.10 with the Atheros driver for my 9285 chipset. When streaming 720p content from my NAS to my htpc (playing in the ever awesome XBMC on my Asrock Ion 330) I experience a lot o buffering. At first I thought it was better to cennect the htpc with a hardwire, eventhough both my router and the Atheros chipset allow for a wireless N connection.

However, I tried how streaming 720p content would perform under Windoze 7, and quess what, no buffering problems whatsoever. I also experience stuttering on playing music from the NAS every now and then. This isn't the case under Windows as well.

Below are the outputs of lshw and iwconfig. Is there anyone that has got an idea on how to get better performance out of the Atheros chipset under Maverick? It's a shame that I will have to switch to Windows to be able to watch I movie or listen to some music without the annoyance of constant buffering. It might be useful to add that I am on the Mint (Linux Mint 10) variant of Maverick with a 2.6.35-22-generic version of the linux kernel.

lshw
```
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:3c:5b:6e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.14.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:febf0000-febfffff
```

iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"AP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 74:22:3A:11:48:C8   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by HydroDiOxide on 2011-06-17
I installed the compat-wireless package which gave me a new module for the atheros 9285 and the 2.6.35-28 kernel version. My streaming issues are a lot better now. I noticed it only once.

---

### Post by Perfect Storm on 2011-06-17
Moved to Other OS/Distro Talk.

---

