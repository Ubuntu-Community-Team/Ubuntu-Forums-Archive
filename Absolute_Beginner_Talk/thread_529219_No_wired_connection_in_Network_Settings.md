---
title: "No wired connection in Network Settings"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by mdoyle on 2007-08-18
Hey all. I just installed a fresh copy of Feisty on a machine. I'm having problems getting it to connect to my Wireless connection so I figured i'd plug in  network cable until I could get that figured out only to see that there is no Wired Connection in the Network Settings screen. 

This is only my second install of Ubuntu, and I have no idea how to get my Wired Connection to work. Thanks in advance.

---

### Post by steveneddy on 2007-08-18
Try plugging in the wired connection and restarting.

---

### Post by mdoyle on 2007-08-19
That was the first thing I tried.

---

### Post by Raptor45 on 2007-08-19
Are you sure the network card is functional?

What does ifconfig show in the terminal?

---

### Post by mdoyle on 2007-08-19
I know the card works (not broke), since it works in Vista. ifconfig just lists "lo" and "ra0" which is the wireless card.

---

### Post by mdoyle on 2007-08-19
?

---

### Post by schorsch on 2007-08-19
Please type
```
lspci
```
and post the output here.

---

### Post by mdoyle on 2007-08-19
00:00.0 Host bridge: Intel Corporation Uknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Uknown device 29c1 (rev 02)
00:03.0 Communication controller: Intel Corporation Uknown device 29c4 (rev 02)
00:19.0 Ethernet Controller: Intel Corporation Uknown device 294c (rev 02)
00:1a.0 USB Controller: Intel Corporation Uknown device 2937 (rev 02)
00:1a.1 USB Controller; Intel Corporation Uknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Uknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Uknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Uknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Uknown device 2940 (rev 02)
00:1c.1 PCI bridge: Intel Corporation Uknown device 2942 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Uknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Uknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Uknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Uknown device 2934 (rev 02)
00:1d.1 USB Controlle: Intel Corporation Uknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Uknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Uknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Uknown device 2912 (rev 02)
00:1f.2 SATA controller: Intel Corporation Uknown device 2922 (rev 02)
00:1f.3 SMBus: Intel Corporation Uknown device 2930 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0295 (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Uknown device 6101 (rev b1)
07:01.0 Network Controller: RaLink RT2500 802.11g cardbus/mini-PCI (rev 01)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by schorsch on 2007-08-19
> **mdoyle said:**
> 
00:19.0 Ethernet Controller: Intel Corporation Uknown device 294c (rev 02)

I guess here is the problem: There is no driver for your wired network adapter as your board is to new. I just searched the forum for "294c" and got several hits like [this one]("http://ubuntuforums.org/showthread.php?t=492907&highlight=294c")
Perhaps you can look in the other threads if someone has found a solution (just got lazy ;-) ) but it is mentioned that your card will work in Gusty.

---

### Post by mdoyle on 2007-08-19
Thanks for the help. Looks like i'll just move straight to Gutsy.

---

