---
title: "wireless messed up..."
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-11-04
When I run:
```
john@laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:XXXX-XXXX-XX (shows the correct one)
          Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```
How does one associate the access point?

---

### Post by Neobuntu on 2006-11-04
If I understand you correctly, since your wireless NIC seems to be installed, run "Network Settings" and type in your wireless net name. AKA your SSID. Also; in your router (at "192.168.1.1" in Firefox maybe, if not ...0.1 or ...2.1), you'd match this SSID name (and also set a router password; for your health please.)

If you want to get all technical (But need not, so don't.), the configuration file is "/etc/network/interfaces" where you would find "wireless-essid linksys" (change "linksys" to your SSID) under eth1(for your wireless card). yet, this leads to typos and you need not get all Slackware up on it. :) See above instead.

---

### Post by Papa-san on 2006-11-05
Thanks... Unfortunately, I have already done these things to no avail.I am trying to work through this in the wireless forum: [http://www.ubuntuforums.org/showthread.php?t=293218](http://www.ubuntuforums.org/showthread.php?t=293218)

EDIT: So far, no success!

---

### Post by Neobuntu on 2006-11-05
Remove the BCM43XX device and ask you seller for a replacement that is known to work without having open software developers reverse engineer the darn thing. Intel wireless devices are known to work. Dell gave me one FOR FREE and didn't even want the Broadcom/conexant POS back! I still don't like Dell, but they are learning.

STOP wasting time with it. I know it's not fair but you can replace that device for $20. If you choose wisely, it (the driver module) just works.

Avoid crappy chip-sets from crappy ill supported manufactures. Always Google your prospective chip-set for open compatibility and user ease. If you can't tell what chip-set it has, don't buy it! This includes new computers kids.

---

### Post by Papa-san on 2006-11-06
I know...

What has me bothered is that it was working flawlessly until I had to switch to DSL. I am pretty sure I just have some leftover info in files that keep it from working right with the new router...

---

