---
title: "Wireless (BCM4318) Connectivity Problem"
date: 2006-08-20
forum: Apple PPC Users
---

### Post by smbrow14 on 2006-08-20
I have an iBook G4 that I recently installed Ubuntu 6.06 on to. I have a wireless network at home and I'm trying to get Ubuntu on my Mac to connect to it. After browsing through the forums I found the relevant posts concerning bcm43xx-fwcutter and /lib/firmware. I followed the directions, commented out the wireless references in the /etc/network/interfaces. I also installed the network-manager-gnome applet. After rebooting Ubuntu detected my home network (Doodie, which has MAC filtering but no WEP key right now), and connects to it. The connection lasts for maybe 3-4 minutes and then stops responding. While the connection is working I can browse the internet fine. 

From what I've gathered in other posts, the output from dmesg may be relevent: (Note: eth0 is ethernet connection, eth1 is wireless)

```

[   81.854538] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   81.854546] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.854617] IPv6 over IPv4 tunneling driver
[   99.957352] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[   99.958220] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[   99.959017] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  103.552031] SoftMAC: Open Authentication completed with 00:12:17:3c:eb:ad
[  103.606819] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  113.726996] eth1: no IPv6 routers present
[  125.935007] eth1: no IPv6 routers present
[  166.375162] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  170.986971] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  170.987721] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  170.989334] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  455.072184] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  455.074668] SoftMAC: Authentication response received from 00:90:4b:d5:05:f4 but no queue item exists.
[  492.171313] bcm43xx: Card IRQ register not responding. Giving up.
[  493.387539] bcm43xx: Card IRQ register not responding. Giving up.
[  553.541385] bcm43xx: Card IRQ register not responding. Giving up.
[  556.403004] SoftMAC: Authentication timed out with 00:12:17:3c:eb:ad
[  578.485048] bcm43xx: Card IRQ register not responding. Giving up.
[  596.483130] eth0: Link is up at 100 Mbps, full-duplex.
[  596.483145] eth0: Pause is disabled
[  596.487016] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  603.451350] bcm43xx: Card IRQ register not responding. Giving up.
[  607.010994] eth0: no IPv6 routers present
[  628.647175] bcm43xx: Card IRQ register not responding. Giving up.
[  634.909311] eth0: Link is up at 100 Mbps, full-duplex.
[  634.909330] eth0: Pause is disabled
[  645.362997] eth0: no IPv6 routers present
[  753.669337] bcm43xx: Card IRQ register not responding. Giving up.

```

I'm pretty much at a loss at this point. If there's any information missing that I can post to help clarify what the problem may be please let me know. Any and all ideas are certainly welcome! Thank you.

---

### Post by smbrow14 on 2006-08-20
I'm connected wirelessly right now (not sure how long it will last though)****. Here is my iwconfig output:

```

stephen@stephen-iBook-G4:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Doodie"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:12:17:3C:EB:AD
          Bit Rate:11 Mb/s   Tx-Power=17 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=185/100
          Rx invalid nwid:0  Rx invalid crypt:10  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

### Post by smbrow14 on 2006-08-20
OK, I guess I need to do a bit of reading on wireless networks. I've been sitting right next to the wireless router and my connection has been fine. I walked to the other side of the apartment with the Mac and the connection died. Strange, seeing as how I get 100% strength from twice that distance under OS X (small apartment ;). Perhaps it's a limitation with 802.11/b?

---

### Post by trubblemaker on 2006-11-08
the signal lies on the broadcom cards.  As they backwards implemented the driver the signal strength isn't something they've fixed yet.  to get more dependablitity out of your driver, if the rate isn't already set you may need to change it to 11M

```
 sudo iwconfig wlan0 rate 11M 
```

if you want even more dependability and speed you should switch to ndiswrapper.  Unfortunately the native driver isn't up to snuff quite yet.  sorry about the late response.

---

