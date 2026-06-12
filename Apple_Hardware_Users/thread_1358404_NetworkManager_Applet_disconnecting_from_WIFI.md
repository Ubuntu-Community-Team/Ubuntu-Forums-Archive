---
title: "NetworkManager Applet disconnecting from WIFI"
date: 2009-12-18
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2009-12-18
Since I updated from Jaunty to Karmic my WIFI keeps disconnecting frequently. 

Using wicd this is not happening. So I believe NetworkManager applet is responsible for the problem. 

My syslog:
```
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): device state change: 8 -> 3 (reason 11)
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): deactivating device (reason: 11).
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 9255
Dec 18 17:06:05 hal9000 NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 18 17:06:05 hal9000 avahi-daemon[1048]: Withdrawing address record for 62.213.144.27 on eth1.
Dec 18 17:06:05 hal9000 avahi-daemon[1048]: Leaving mDNS multicast group on interface eth1.IPv4 with address 62.213.144.27.
Dec 18 17:06:05 hal9000 avahi-daemon[1048]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) starting connection 'Auto VF-Guest'
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto VF-Guest' requires no security.  No secrets needed.
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Config: added 'ssid' value 'VF-Guest'
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected
Dec 18 17:06:05 hal9000 NetworkManager: <info>  Config: set interface ap_scan to 1
Dec 18 17:06:05 hal9000 NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Dec 18 17:06:05 hal9000 postfix/master[2518]: reload -- version 2.6.5, configuration /etc/postfix
Dec 18 17:06:20 hal9000 NetworkManager: <info>  eth1: link timed out.
Dec 18 17:07:05 hal9000 NetworkManager: <info>  Activation (eth1/wireless): association took too long, failing activation.
Dec 18 17:07:05 hal9000 NetworkManager: <info>  (eth1): device state change: 5 -> 9 (reason 11)
Dec 18 17:07:05 hal9000 NetworkManager: <info>  Activation (eth1) failed for access point (VF-Guest)
Dec 18 17:07:05 hal9000 NetworkManager: <info>  Marking connection 'Auto VF-Guest' invalid.
Dec 18 17:07:05 hal9000 NetworkManager: <info>  Activation (eth1) failed.
Dec 18 17:07:05 hal9000 NetworkManager: <info>  (eth1): device state change: 9 -> 3 (reason 0)
Dec 18 17:07:05 hal9000 NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Dec 18 17:07:09 hal9000 wpa_supplicant[1287]: No network configuration found for the current AP
Dec 18 17:07:09 hal9000 wpa_supplicant[1287]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 18 17:07:30 hal9000 wpa_supplicant[1287]: CTRL-EVENT-SCAN-RESULTS 

```I do not want to use wicd because NetworkManager allows me to use my Android phone usb-connected to share the mobile network... and wicd do not allows me to do that. So, for me wicd is not a good enough replacement.

Anybody with the same issue?

update: I found a similar report here: [http://ubuntuforums.org/showthread.php?t=1314340](http://ubuntuforums.org/showthread.php?t=1314340)

any solution so far?

---

### Post by tacantara on 2009-12-18
Hmm, I had a problem with Wi-Fi not connecting at all when I upgraded to Karmic, even with a fresh install.  through Google searches, I found links to some tweaks that allowed me to connect with Network Manager.  If I can recall any of them, I will update this post.  Meanwhile, the best I can offer is check out Google.  I'm sure you'll find a plethora of information on Karmic Wi-Fi problems.

I just got the Motorola Droid as an "early Christmas present" from my wife.  I will have to start tinkering with the tethering feature.  The Android OS is just awesome!

---

### Post by octobuntu on 2010-01-01
Please don't ever tell somebody to google a solution to a problem they are a trying to resolve. It's the equivalent of saying, "You have a prooblem? Well just solve it!". It's totally useless to tell somebody to google for an answer; that's how we end up here in the first place!

---

### Post by CodeFarmer on 2011-10-07
*bump*

No joy?

I am having (what I think are) the same symptoms on 100% dist-upgraded Natty... my nm-applet wireless connection stops working after a few minutes (although it still claims to be connected), until I force it to reconnect.

For what it's worth, my connection is to a current-model O2 UK wireless box, that works just fine with my Mac and my girlfriend's Windows.

---

### Post by miatawnt2b on 2011-10-07
you may want to try compiling the latest wl driver on broadcom's website.  That fixed any issues I was having.
-J

---

