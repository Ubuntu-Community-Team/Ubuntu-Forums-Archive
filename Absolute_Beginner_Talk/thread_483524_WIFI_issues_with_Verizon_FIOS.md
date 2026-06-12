---
title: "WIFI issues with Verizon FIOS"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by carl_schulze on 2007-06-24
Had Verizon FIOS installed 1.5 weeks ago, and it works splendidly with with both my laptop and a desktop (both running XP).  Had an old but very nice case sitting around, so I put in an Asus M2N mobo with lots of RAM and a pretty zippy AMD 64 X2 3800 and tossed in an old D-Link DWL-650 wireless PCI card, the kind where you slide a PCIMIA card into the PCI card.  I then loaded Ubuntu Feisty Fawn from a CD ROM disk I downloaded from the 'net on one of my XP machines.  I was ever so pleased how rapidly and smoothly the install went. . . 

until I couldn't get my wireless connection to work.  Odd thing is that Network Settings show a check next to "Wireless connection (wifi0),'" lists the correct ESSID of the FIOS router, but the network icon on the right of the desktop title bar shows the "!" sign, and I can't get onto the net.  Properties  of the "Wireless connection (wifi0)" shows DHCP as the config, and I entered the WEP key I used on the XP systems to connect to the router, but it doesn't seem to work.  I wasn't sure whether I ought to use hex or ascii on the WEP key, so I tried both, but it didn't matter.

Following hints I've gotten elsewhere on Ubuntu, I've tried a "iwconfig" and I think things are OK there.  I get:

lo             no wireless extensions
eth0        no wireless extesions

wifi0 IEEE 802.11b ESSID: "2J2N9" Nickname:""
         mode: managed Freq 2.437 Ghz Access Point: ( a bunch of numbers)
         Bit Rate:11 MB/s     Sensitiviity=1/3
         Retry limit:8 RTS thr: off Frag thr: off
         Power Mgt: off

wifi1 IEEE 802.11b ESSID: "2J2N9" Nickname:""
         mode: managed Freq 2.437 Ghz Access Point: ( a bunch of numbers)
          Bit Rate:11 MB/s     Sensitiviity=1/3
         Retry limit:8 RTS thr: off Frag thr: off
         Power Mgt: off
         Link quality=41/70   Signal level=-59 dBm   Noise level=-100 dBm
         Rx invalid nwld:0  Rx invalid crypt:53   Rx invalid  frag:0
         Tx excessive retries:0   Invalid misc:2   Missed beacon:0


What does all this mean?  It looks to me like it sees the router (which it must have to have obtained the ESSID, cuz I didn't put that in to Ubuntu).  What's going on?  I have another wireless PCI card (Netgear WPN311) which I tried to swap in, but Ubuntu really didn't like me changing hardware on it, I guess, cuz it wouldn't boot, so I went back to the D-Link, got Ubuntu to boot, but the results are exactly as before: no internet.

Carl

---

### Post by NightDevil on 2007-10-28
curious also to the solution but im still searching

---

