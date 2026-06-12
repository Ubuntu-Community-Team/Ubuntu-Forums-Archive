---
title: "no network."
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by shaaheen on 2007-09-08
I juast installed ubuntu 7.04 on a P35 intel mobo , everything came up except for the internal NIC. I am new to Linux and I checked with intel for inf files for linux but no luck. This is a clean install.computer works fine when I hook up the Windows Vista hard drive.:(

---

### Post by overdrank on 2007-09-08
> **shaaheen said:**
> I juast installed ubuntu 7.04 on a P35 intel mobo , everything came up except for the internal NIC. I am new to Linux and I checked with intel for inf files for linux but no luck. This is a clean install.computer works fine when I hook up the Windows Vista hard drive.:(

Hi and welcome, could you post the output of the command
 ```
lspci
```
in the terminal located under applications, accessories, terminal and we can identify your nic card and then maybe help more. And have you check system, administration, network to make sure your wired connection is enabled.

---

### Post by shaaheen on 2007-09-08
here is the lspci dump.
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:03.0 Communication controller: Intel Corporation Unknown device 29c4 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 294c (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.1 PCI bridge: Intel Corporation Unknown device 2942 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 SATA controller: Intel Corporation Unknown device 2922 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0402 (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


And under Network setting it only list the modem setting which I dont have.On the upper right hand corner where it shows a diabled network icon if I click on it, it shows enable automatically.   Hope this will help.:confused:

---

### Post by shaaheen on 2007-09-09
I think I solved the problem.Loaded Gutsy 5 and all is cool.I still have a lot of unkown devices.:):popcorn::guitar:

---

### Post by overdrank on 2007-09-09
> **shaaheen said:**
> I think I solved the problem.Loaded Gutsy 5 and all is cool.I still have a lot of unkown devices.:):popcorn::guitar:

Hi you can update your pci ids with this command in the terminal 
```
sudo update-pciids
```

---

