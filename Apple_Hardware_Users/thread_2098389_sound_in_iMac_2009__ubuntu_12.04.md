---
title: "sound in iMac 2009 / ubuntu 12.04"
date: 2012-12-26
forum: Apple Hardware Users
---

### Post by aswinsainarain on 2012-12-26
Dear all

I just installed Ubuntu 12.04 on my iMac 20", purchased in 2009.

The problem of sound in iMacs running Ubuntu seems to be common with many solutions. However, I seem to have a slightly different problem. I have tried various snd-hda-intel model options, but with most (e.g. imac24), my headphones seem to be fine, but the internal speakers do not work at all. Audio input is also OK, at least with imac24. 

I really do not want to have to connect a fat external speaker to the headphone jack. Any advice on how I might get the internal speakers to get going will help.

Thanks,
Aswin

---

### Post by powerpcliberation on 2012-12-27
Can you first tell us what shows up for your sound controller in the system profile.

---

### Post by aswinsainarain on 2012-12-27
> **powerpcliberation said:**
> Can you first tell us what shows up for your sound controller in the system profile.

When I give lspci, I get the following (full output below; I do not seem to get a "Multimedia audio controller"):

"00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)"

In ALSA Mixer, I have the following:

Chip: "Realtex ALC889A".
Card: "HDA NVidia"

Thanks,
Aswin

Full output from lspci:
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: NVIDIA Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400] (rev b1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 07)

---

### Post by aswinsainarain on 2012-12-27
The issue seems to have been resolved.

I managed to somehow find out that my iMac was called iMac 9.1. Setting the model to imac91 in modprobe.d/options.conf got it working.

Thanks,
Aswin

---

### Post by powerpcliberation on 2012-12-28
Glad you found a fix.  Config files are about the best/easiest way to get things just the way you want/need.

Try mouseemu for more controls over the mouse.  It's config based also.

---

