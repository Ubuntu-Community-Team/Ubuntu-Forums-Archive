---
title: "Trying to set up multiple monitors"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by r691175002 on 2007-10-08
Hi, I have been trying to set up a triple monitor setup on Ubuntu, and have been so far failing miserably.

I have gotten down to the point where I am trying to use nvidia-settings, however whenever I try to run it it outputs a bunch of errors:

```
sudo nvidia-settings

ERROR: Error parsing configuration file '/home/r691175002/.nvidia-settings-rc'
       on line 10: 'RcFileLocale = en_CA.UTF-8' (Unrecognized attribute name).

ERROR: NV-CONTROL extension not found on this Display.

ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.

ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

```

All I want is to have my other two monitors working, I have two Nvidia 8600Gt cards, and three monitors.

As another question, how do I get what BusID the video cards are running on?  lspci (or whatever it is) just outputs tonnes of stuff, and I cant see "Video" anywhere in there.  Xorg.conf identifies one of my cards as 10:0:0 which I can't even find on the lspci list.
```
lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)
04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
0a:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)

```

I was using Ubuntu for a few months on another computer (but I still have no idea what I am doing terminal-wise), and like it enough that I spent today and two reinstalls of Ubuntu (I didn't know about sudo dpkg-reconfigure) trying to get it to work.  It's really starting to frustrate me.

Thanks

---

### Post by overdrank on 2007-10-08
> **r691175002 said:**
> Hi, I have been trying to set up a triple monitor setup on Ubuntu, and have been so far failing miserably.

I have gotten down to the point where I am trying to use nvidia-settings, however whenever I try to run it it outputs a bunch of errors:

```
sudo nvidia-settings

ERROR: Error parsing configuration file '/home/r691175002/.nvidia-settings-rc'
       on line 10: 'RcFileLocale = en_CA.UTF-8' (Unrecognized attribute name).

ERROR: NV-CONTROL extension not found on this Display.

ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.

ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

```

All I want is to have my other two monitors working, I have two Nvidia 8600Gt cards, and three monitors.

As another question, how do I get what BusID the video cards are running on?  lspci (or whatever it is) just outputs tonnes of stuff, and I cant see "Video" anywhere in there.  Xorg.conf identifies one of my cards as 10:0:0 which I can't even find on the lspci list.
```
lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
[COLOR="Red"]01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)[/COLOR]
04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
[COLOR="Red"]0a:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)[/COLOR]

```

I was using Ubuntu for a few months on another computer (but I still have no idea what I am doing terminal-wise), and like it enough that I spent today and two reinstalls of Ubuntu (I didn't know about sudo dpkg-reconfigure) trying to get it to work.  It's really starting to frustrate me.

Thanks

Hi I have highlighted your graphics cards and if you will run the command in the terminal 
```
sudo update-pciids
``` This will update your pci ids and you will be able to see your cards in those lines. As for multiple monitors you may find some help in this thread
[http://ubuntuforums.org/showthread.php?t=221174&highlight=twin+view](http://ubuntuforums.org/showthread.php?t=221174&highlight=twin+view)
Good luck! :KS

---

