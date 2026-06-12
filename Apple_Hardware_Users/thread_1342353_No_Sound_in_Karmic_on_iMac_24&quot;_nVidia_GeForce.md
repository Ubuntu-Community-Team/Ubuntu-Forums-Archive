---
title: "No Sound in Karmic on iMac 24&quot; nVidia GeForce 9400M"
date: 2009-11-30
forum: Apple Hardware Users
---

### Post by timmacfarlane on 2009-11-30
Hi, I have an early 2009 iMac with nVidia GeForce 9400M. I've just installed Karmic Koala on it and I have no sound. I've tried the modprobe.d/alsa-base.conf tricks as described in [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac) with no success. Anybody have similar problems and a fix? Anybody know which module I should be using for sound?

lspci says:

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400] (rev b1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)

---

### Post by jamesey on 2009-11-30
check out this thread. 
I got headphones working but if you're savvy enough to apply a patch, you can get the imac speakers to work


[http://ubuntuforums.org/showthread.php?t=1096802](http://ubuntuforums.org/showthread.php?t=1096802)

---

### Post by linuxopjemac on 2009-12-01
you can also look at this thread:
[http://forums.fedoraforum.org/archive/index.php/t-232842.html](http://forums.fedoraforum.org/archive/index.php/t-232842.html)

```
gedit /etc/modprobe.conf
```

Add this line:

```
options snd-hda-intel model=auto 3stack-6ch
```

save and reboot. switch Channels from 2ch to 6ch in alsamixer
(you might have to do this with alsamixer, don't know)

```
pulseaudio -k
```

in gnome-volume-control you will see Surround Sound 5.1
After switch Channels from 2ch to 6ch you run

```
alsactl store
```

to save the changes you made for when you reboot

---

