---
title: "Ethernet card not working"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-05-09
When i installed ubuntu my ethernet card stopped working, im currently running a dual boot of edgy/xp and the card works just fine in xp
its a belkin card based on the realteck 8139 chipset
the computer knows there is something there when i run *lspci* but it doesnt show up in the networking tools or anywhere else
i know the drivers are meant to be already installed but it still isnt working
does anyone have any idea about what to do?

---

### Post by overdrank on 2007-05-09
> **simon303 said:**
> When i installed ubuntu my ethernet card stopped working, im currently running a dual boot of edgy/xp and the card works just fine in xp
its a belkin card based on the realteck 8139 chipset
the computer knows there is something there when i run *lspci* but it doesnt show up in the networking tools or anywhere else
i know the drivers are meant to be already installed but it still isnt working
does anyone have any idea about what to do?

Hi I have done a few searches on that chipset and it does not look good. I did not find anything that had a solutions to fix it. So this link may help you find a card that will work!
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Good luck !

---

### Post by simon303 on 2007-05-09
But according to [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek) this chipset is supported

---

### Post by Seisen on 2007-05-09
Try going to System>Administration>Network and see if you card is shown there.

---

### Post by simon303 on 2007-05-09
its not in networking

but *lspci -v* gives me
```
simon@simon-desktop:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
        Flags: bus master, medium devsel, latency 120
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at eddff000 (32-bit, prefetchable) [size=4K]
        I/O ports at dc00 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 120
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ede00000-efefffff
        Prefetchable memory behind bridge: d5c00000-e5cfffff

00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at f000 [size=16]

00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
        Flags: medium devsel

00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 16, IRQ 11
        Memory at efffe000 (32-bit, non-prefetchable) [size=4K]

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Belkin F5D5000 PCI Card/Desktop Network PCI Card
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at de00 [size=256]
        Memory at efffff00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at effe0000 [disabled] [size=64K]
        Capabilities: <access denied>

01:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at efef0000 [disabled] [size=64K]
        Capabilities: <access denied>
```

so it is there

---

### Post by jerrylamos on 2007-05-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82927](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/82927) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				On my Realtek card, during boot Feisty 7.04 Network Manger disables eth0.  I can see this by looking in /var/log/syslog and searching for either Network Manager or eth0 or Realtek.

There's a couple solutions I use: on the top line to the right there's an icon looking like a monitor, or actually two of them one behind the other.  After boot, it has a tiny red mark on it.  If I put my cursor on the icon, it says "No wired connection".  So I click on it.  It gives a little pull down menu including Wired Network.  I click on that.  Then the icon does a whirl and connects to the network.  All this takes less time than it does to read the paragraph.

Another way is to do Applications, Accessories, Terminal
sudo dhclient
password
which also works.  Do note that in this case the red mark stays on the little Network "Mangler" icon.

Do note how many entries there are in the launchpad bug link.....

Cheers, Jerry:(

---

### Post by simon303 on 2007-05-09
im using edgy and cant see a similar icon in network manager

had a look in  /var/log/syslog and found no mention of network manaer, eth0, realtek or belkin

i have tried *dhclient* and it says ```
no broadcast interfaces found - exiting
```

---

