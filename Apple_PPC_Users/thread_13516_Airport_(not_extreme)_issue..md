---
title: "Airport (not extreme) issue."
date: 2005-02-01
forum: Apple PPC Users
---

### Post by Darksev on 2005-02-01
So I probably did something dumb, but eh, this is how we learn. Initially, my wireless network connection was working just fine right from install, but I just had to mess with things. 

My network layout was originally a bit odd. Netgear DLS/Cable router attached to cable modem and PC1 (downstairs) with ports 2 and 3 running upstairs to PC2 and the WAN port on a Dlink Wireless router. with this configuration, I was able to connect wirelessly on my ibook running warty, but I was unable to see my windows network from any OS on the ibook (OS X, YDL, then Warty). 

Thinking this must have something to do with the way I had the Dlink set up using the WAN port, I connected the cable to the downstairs router to port 1 (AP mode?).
suddenly, Wireless internet no longer works on the ibook.

Comp>config>network shows Eth1 as an available wireless device. Wireless app in gnome panel shows 90% connection. IWCONFIG shows:

```
eth1
IEEE 802.11-DS  ESSID: "SevWLAN" Nickname: "HERMES I"
Mode:Managed   FrequncyL 2.437GHz  Access Point: 00:11:95:39:24:DD
Bit Rate: 11Mb/s  TX-Power=15 dBm  Sensitivity:1/3
Retry limit:4  RTS thr:off   Fragment thr:off   Power Management: off
Link Quality=42/92   signal level=-57 dBm   Noise level=-99 dBm
Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
Tx exessive retries:0   invalid misc:0   missed beacon:0
```


my interfaces file:

auto eth1
iface eth1 inet dhcp
name Wireless LAN card
wireless_mode managed
wireless_essid SevWLAN
wireless_channel 6

I know I can probably go back to connecting my windows network to the Dlink via the WAN port and get my internet back, but that would take me back to square one in getting ubuntu access to my windows network. any help would be appreciated.

Edit----
yea, plug the cable from main router back into WAN port, and bam, network is back, no setting changes. wtf is up with that :/ still no help to getting me access to  my windows shares

---

