---
title: "Audio Jack Trouble on MacBook 5,2"
date: 2014-09-02
forum: Apple Hardware Users
---

### Post by Miles_Steele on 2014-09-02
Hi all,

I have a MacBook 5,2 running Ubuntu Server 14.04.
The sound from the internal speakers works fine (using mplayer), but when I try to play on some external speakers from the audio jack it's silent.

I have already tried a few things:
- Toggling the S/PDIF related items in alsamixer causes the red (optical signal) light to toggle.
- Adding various lines like "options snd-hda-intel power_save=10 power_save_controller=N model=mb5" to /etc/modprobe.d/alsa-base.conf and rebooting.
- Toggling Auto-Mute in alsamixer causes the internal speakers to play while the jack is plugged in, but the external speakers remain silent.

Any ideas for how to fix external audio? Also, are there any logs I can look at to debug this further?

Thanks in advance,
- Miles

Output of various system description commands:
```

$ lspci
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400M G] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW533 [TrueFire] PCIe 1394a Controller (rev 07)

```

```

$ uname -a                             
Linux jukebox 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ sudo dmidecode -s system-product-name 
MacBook5,2

```

---

