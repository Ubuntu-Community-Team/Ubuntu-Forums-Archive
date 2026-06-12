---
title: "No sound atall"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-05
Just swapped to Ubuntu from Vista. Everythings going fine except that I get no sound playing videos or audio files. Do I need a driver? Where can I find it?

---

### Post by n00buntu_tim on 2007-12-05
Uncheck the "digital i/o" checkbox under sound properties.

---

### Post by gleble on 2007-12-05
wher do I find sound properties?

---

### Post by DragonKore on 2007-12-05
Double-click the speaker icon in the upper right. Then go to the far right tab.

---

### Post by gleble on 2007-12-05
That takes me to a mixer. Turned everything up. No luck

---

### Post by DragonKore on 2007-12-05
There should be tabs at the top of the mixer, and the far right one (I can't recall the name of it and I'm not in Linux right now) has the Digital I/O option.

---

### Post by gleble on 2007-12-05
the tabs are file edit and help, none of them help

---

### Post by FuturePilot on 2007-12-05
Can you post the output of
```
lspci
```
This will show what kind of hardware we're dealing with.

---

### Post by gleble on 2007-12-05
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

### Post by DragonKore on 2007-12-05
> **gleble said:**
> the tabs are file edit and help, none of them help

Oh, you must have a different version of Alsa than I do. Perhaps you can update it through Synaptic.

---

### Post by FuturePilot on 2007-12-05
Try this
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add this line to the end
```
options snd-hda-intel position_fix=1 model=3stack
```
Save and reboot. See if that does the trick.

---

### Post by gleble on 2007-12-05
there are lots of alsa s  which one do you mean?

---

### Post by gleble on 2007-12-06
Synaptic lists several programs under alsa which one do I want to get your tabs?

---

### Post by gleble on 2007-12-06
Future Pilot I tried  and it didn't work. Any other ideas?

---

### Post by kpkeerthi on 2007-12-06
Try installing linux-ubuntu-modules from synaptic

---

### Post by gleble on 2007-12-06
Installed all linux-ubuntu-modules and rebooted. No luck

---

### Post by FuturePilot on 2007-12-06
Try this
```
sudo apt-get install linux-backports-modules-generic
```
Then reboot.

---

### Post by gleble on 2007-12-06
Done, still doesn't work. Sorry to be so negative, I'm lost here.

---

### Post by gleble on 2007-12-07
I thought installing oss might help. Why do I get this error?

neil@neil-laptop:~$ sudo sh /usr/lib/oss/build/install.sh
sh: Can't open /usr/lib/oss/build/install.sh

---

### Post by gleble on 2007-12-09
I'm trying to change the alsamixer. It says off-hook is off. Should it be on? How do I change it.? Still stuck on the error messages in the last post.

---

### Post by gleble on 2007-12-09
Finally worked out how to change settings in alsamixer. It's always the simple things. Thanks to all that helped.

---

