---
title: "ubuntu 8.04 on acer 4520"
date: 2008-06-09
forum: Absolute Beginner Talk
---

### Post by ddg on 2008-06-09
Hi,

I have installed ubuntu 8.04 desktop version on acer 4520.
Every thing is running except:
- Wireless LAN, Web camera and the nvidia GE 7000 VGA card is not detected.

The screen is running with resolution of 800 x 600.

I am very new to linux and want to understand linux properly

Regards,
ddg

---

### Post by Joeb454 on 2008-06-09
Post the output of ```
lspci
``` From a terminal - don't forget to use the [code] tags too.

And have you installed the Nvidia restricted drivers for your nvidia card?

---

### Post by ddg on 2008-06-09
> **Joeb454 said:**
> Post the output of ```
lspci
``` From a terminal - don't forget to use the [code] tags too.

And have you installed the Nvidia restricted drivers for your nvidia card?

 lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I did not installed any nvidia restricted driver.
rgds,
ddg

---

### Post by ddg on 2008-06-10
Hi any body there,

I need help to install nvidia driver for acer 4520, to active the wireless and web cam too.

rgds,
ddg

---

### Post by ricflomag on 2008-06-16
Hi there, i've just installed hardy on an acer 4520-5881 bought with Linpus Linux preinstalled:

 * The nvidia driver (Geforce 7000M) installs perfectly using the restricted drivers manager.
 * The webcam works out of the box (tested in Ekiga and Skype).
 * I'll post here how to install the wireless driver later tonight, but you should find the answer in this forum looking for "Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)".

As for now, the only problem i'm having is with the microphone (build-in or in-line). It's mute.

---

### Post by ricflomag on 2008-06-16
Ok, so everything seems to be working fine now.

The following is for installing wireless driver on ubuntu hardy, 64bit version, on Acer 4520-5881, using the device:
```

07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

For the wireless to work, first open synaptic and install "linux-backports-modules-hardy" (The webcam possibly needs it too, but i did not try it before installing this package so i can't tell).

Still in synaptic, install "ndiswrapper-utils-1.9".

Make sure that the wireless IS NOT installed in the restricted drivers manager. (Reboot if necessary after having removed the drivers).

Now we'll download the windows driver for the wireless device and install it through ndiswrapper. Open a terminal window and type, one line after another:
```

wget -c [http://vostorga.org/files/ar5007eg-64-0.2.tar.gz](http://vostorga.org/files/ar5007eg-64-0.2.tar.gz)
tar xvfz ar5007eg-64-0.2.tar.gz
sudo ndiswrapper -i ar5007eg-64-0.2/ar5007eg/net5211.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```
(some of these things can be done through the graphical interface, but it is more straightforward using the command line ;))

This should be enough, at this point the wireless device should be activated. If not, do the last step and reboot.

For it to be activated at each boot, add a line to /etc/modules, opening the text editor as an administrator:
```

sudo gedit /etc/modules

```

and insert the "ndiswrapper" on a new line at the end (without quotes).

Reboot to check if everything goes fine.

There are plenty of posts in these forums about installing wireless drivers, this one might be redundant, let's hope it does not add confusion ;)

---

### Post by ricflomag on 2008-06-16
I did not mention that the microphone does work fine. I had just messed up with the volume control settings. :)

---

### Post by manishanchan on 2008-06-17
Well i dont know much about that but it might be the latest version

---

### Post by dBOMB on 2008-06-17
soo ubuntu works on acer.. im having issues in a acer 5050

i cant get passed i guess some kind of bug..

Bug: Softlockup- CPU#1 stuck for 11s [MODPROBE:1283]

---

### Post by ddg on 2008-06-23
Hi ricflomag,

Sorry, I was away for a week and did not try the solution you gave. Btw, I use 32 bit version of ubuntu instead of 64 bit.
I am not sure about ip setting 64 bit O/S, is it the same??

Yesterday, I tried using madwifi driver with steps given by nicedude.
The wireless worked well with wicd manager until I install the nvidia driver. After nvidia driver, the wireless device is not detected again.

regards,
ddg

[QUOTE=ricflomag;5201138]Ok, so everything seems to be working fine now.

The following is for installing wireless driver on ubuntu hardy, 64bit version, on Acer 4520-5881, using the device:
```

07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

---

### Post by ddg on 2008-06-24
> **ricflomag said:**
> I did not mention that the microphone does work fine. I had just messed up with the volume control settings. :)

Hi ricflomag.
 
I managed to get it working with madwifi driver.
rgds,
ddg

---

### Post by sherl0k on 2008-07-11
anyone know how to get the IR port working?

---

### Post by satauros on 2008-07-11
what kind is it?

---

