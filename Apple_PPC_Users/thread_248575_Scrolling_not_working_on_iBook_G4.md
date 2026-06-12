---
title: "Scrolling not working on iBook G4"
date: 2006-09-01
forum: Apple PPC Users
---

### Post by Zwerver on 2006-09-01
Hi :) I've seen the various posts and I tried to compile my own drivers e.g. but I'm still not able to using the "magic two fingers"-scrolling with Ubuntu at my iBook G4 :( 

I have the following modules loaded:

> 
Module                  Size  Used by
hci_usb                18452  2 
rfcomm                 48216  0 
l2cap                  28484  5 rfcomm
bluetooth              62180  7 hci_usb,rfcomm,l2cap
uinput                 10880  2 
ppdev                  11748  0 
lp                     13804  0 
parport                45936  2 ppdev,lp
radeon                136968  1 
drm                    90744  2 radeon
cpufreq_userspace       5640  1 
cpufreq_stats           6276  0 
cpufreq_powersave       1920  0 
cpufreq_ondemand        8284  0 
cpufreq_conservative     9764  0 
ipv6                  323492  6 
dm_mod                 69808  1 
md_mod                 89336  0 
sbp2                   28068  0 
scsi_mod              179588  1 sbp2
apm_emu                 8364  0 
snd_powermac           57920  1 
snd_pcm_oss            68480  0 
snd_mixer_oss          23072  1 snd_pcm_oss
snd_pcm               109892  2 snd_powermac,snd_pcm_oss
snd_timer              29188  1 snd_pcm
snd                    72532  7 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11716  1 snd
snd_page_alloc         12424  1 snd_pcm
appletouch              9664  0 
af_packet              27080  4 
uhci_hcd               46896  0 
sungem                 38948  0 
sungem_phy             10432  1 sungem
uninorth_agp           11432  1 
agpgart                39900  2 drm,uninorth_agp
bcm43xx               136524  0 
ieee80211softmac       33568  1 bcm43xx
ieee80211              39784  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7136  1 ieee80211
evdev                  12608  13 
tsdev                   9440  0 
ext3                  166824  2 
jbd                    72436  1 ext3
usbhid                 51844  0 
ohci1394               42868  0 
ieee1394              436560  2 sbp2,ohci1394
ehci_hcd               39272  0 
ohci_hcd               25732  0 
usbcore               156576  7 hci_usb,appletouch,uhci_hcd,usbhid,ehci_hcd,ohci_hcd
ide_disk               20800  4 
ide_cd                 38372  0 
cdrom                  49500  1 ide_cd
i2c_keywest            11936  0 
capability              5352  0 
commoncap               8256  1 capability


the error in /var/log/Xorg.0.log:

> 
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"

Kernel version:
> root@delta:~# uname -a
Linux delta 2.6.15-26-powerpc #1 Thu Aug 3 02:53:39 UTC 2006 ppc GNU/Linux
root@delta:~# 


This looks to me that the synaptics driver is still not correct, but isn't this fixed in Draper (6.06.1-LTS)?

Does anyone has a solution for me?


ot@delta:~# lspci 
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
root@delta:~# 
[/quote]
----

lspci:

> 
ronald@delta:~$ lspci 
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
ronald@delta:~$ 

---

