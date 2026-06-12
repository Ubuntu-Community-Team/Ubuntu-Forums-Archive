---
title: "Ubuntu successfully installed.....but..."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by mervo1944 on 2008-01-01
Internet connection achieved only via the ethernet cable.  So what I attempted to do was
to install the CD D-Link drivers using Wine. Successful to the point where a message told me
to reboot to complete the process.

When I rebooted, I saw a 'wireless connection manager' icon on the desktop. I clicked on it
and was confronted by a very small rotating icon followed seconds later by an ominous 'beep'.
In other words it wouldn't open.

If someone can tell me how this can be fixed, I'd be mighty grateful. Especially if the drivers need
to be installed in a specific directory.

Also, typing ndisgtk resulted in the message "Root or Sudo privileges required". An internet
search in order to get over this problem made my brain hurt. so if any one can post a simple quick
fix by way of a command I'd be over the moon.  It would mean that I could operate my computer
from inside my newly constructed and be able to evade my two sons watching the Disney Channel !
:)

---

### Post by RomeReactor on 2008-01-01
Hi. NdisGTK should be located in "System->Administration->Windows Wireless Drivers". You might need the .INF and .SYS files from your drivers CD in order to get your wireless card going, or perhaps others, depending on the card's particular model; please open a terminal (Applications->Accessories->Terminal) and post the output of this:
```
lspci
```

---

### Post by kleo skywalker on 2008-01-01
I connect to the internet using a D-link modem or router (can't remember which) via ethernet. I never needed to install any drivers. I just went to System-->Administration-->Network and configured the "Wired Connection". (I used set it to "Static IP" but I think that depends on your internet service provider.)
Then I ran ```
sudo pppoeconf
``` like it says in the help manual.
After rebooting, I could connect to the internet.

---

### Post by mervo1944 on 2008-01-01
Thanks. Typing in ppeoconf gets the response "Looking for ppoe
access concentrator"

I can connect via ethernet cable but not wireless.

So far as I can make out, there isn't a single solution to the message "Root or Sudo privileges required" to the command Ndisgtk.

I tried removing the wireless card and reinserting it in the hope
that Ubuntu would recognise it on a reboot. It didn't

The 'install drivers' icon remains on the desktop and will not open.

At the moment, I've reached what Shakespear describes as a sterile
promentory. :-)

---

### Post by RomeReactor on 2008-01-01
NdisGTK should be in "System->Administration->Windows Wireless Drivers"; opening it from there should prompt you for your password to launch it with administrator privileges. To launch it from the terminal, try:
```
gksudo ndisgtk
```

---

### Post by mervo1944 on 2008-01-02
Thanks.

Typing in the gksudo ndisgtk command brings up the same screen
as going to System/Windows Wireless Drivers. The D-Link drivers I load
are referred to as invalid drivers.

There is an icon on my desktop "Wireless Connection Manager"
I need to open this to complete installation of the wi-fi card drivers.
However, it will not open. All I get is a tiny round rotating icon then a beep.

My Internet guru friend who also has Ubuntu loaded tells me he
can connect wirelessly if I can provide to him my motherboard drivers
(would you believe). I'll have to try and dig them out. :-)

---

### Post by kleo skywalker on 2008-01-02
If I remember correctly, running pppoeconf did something similar on my computer, but at the end internet worked.

---

### Post by mervo1944 on 2008-01-03
Thanks for your help. I've gone as far as I can.
All I can do now is hope my computer guru friend can get me
connected.:(

---

### Post by RomeReactor on 2008-01-03
Posting the result of running **lspci** in the terminal will let us know your wireless card's specific make, model and chipset, so we know what we're dealing with. The drivers you have installed through ndiswrapper are not working, and this is not uncommon with using drivers from the CD. Also, windows drivers won't work with Wine; that's what ndiswrapper is for. So please post the output of:
```
lspci
```
so more people will be able to assist you.

---

### Post by mervo1944 on 2008-01-03
Here goes. I had to cut and past to the Ubuntu text editor
and save it to the windows documents and settings directory, so I hope it doesn't get lost in the translation. :-)

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)
01:01.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)
merv@merv-desktop:~$

---

### Post by D_invictus on 2008-01-03
I've searched all over the internet for instructions to configure my atheros wireless.
My output was

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
dave@dave-laptop:~$ 

Can anyone help me?

---

### Post by LowSky on 2008-01-03
This is the wireless card

14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
try these directions

[http://ubuntuforums.org/showthread.php?t=554531](http://ubuntuforums.org/showthread.php?t=554531)

---

### Post by RomeReactor on 2008-01-03
mervo, this is your card:
> 01:00.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)

By looking at other threads here it seems your card does not work with ndiswrapper and window drivers; [there is a patch for the MadWifi driver]("http://ubuntuforums.org/showthread.php?p=3884923&highlight=AR5416#post3884923") that seems to work for some. You'll need to install the build-essential package along with kernel headers for it to compile:
```
sudo apt-get install buoild-essential linux-headers-`uname -r`
```

I have to go now; I'll return later to see if I can help further.

---

