---
title: "[SOLVED] Wireless Card Help?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ZOOstation on 2007-12-26
Hi, I'm sorry to post yet another of what I know are very similar topics. I've been going through all of them and trying to find something that works and maybe I just misunderstood something but I've had no luck so far.

I use an HP Pavilion zd8000 with a built-in wireless network card BCM4306 802.11b/g Wireless LAN Controller. I just replaced Windows XP with Ubuntu 7.10 Gutsy Gibbon.

Not only have I encountered most people's problem of getting the computer to recognize the wireless card and locate my wireless network, but whenever I restart the computer it forgets it all and can't even recognize the card again. I've so far had to completely uninstall and reinstall ndiswrapper and reintroduce the original windows .inf file from cd, plus lots of terminal coding that I don't understand enough to remember or recognize it when I look for it again on these forums.

Can somebody please help me through this? I'm new to linux, but I'm a quick learner at this kind of stuff.

Thank you so much.

---

### Post by wormser on 2007-12-26
I have a BCM4309 which is similar to yours.  I installed mine with restricted drivers.  System> Administration> Restricted Drivers.  You will need to be online to download a file in the wizard.  If you cannot get online then here is a link to the file you need.  [http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o).  If you go through the wizard you will see it is the same link.

---

### Post by xeth_delta on 2007-12-26
Hi, welcome to the forum! Could you please open a terminal or cosole and execute the following commands one by one:

```
lspci
lsusb
lshw -C net
```

Post between code tags (the # button in the post page) the output of these commands.

Xeth

---

### Post by ZOOstation on 2007-12-26
lspci:

```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

lsusb:

```
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

lshw -C net

```
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:99:0f:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.64 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:bb:c1:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
```

Presently, it recognizes the device but cannot find the network. As I said, I expect it will forget the device when I turn the computer off.

---

### Post by xeth_delta on 2007-12-26
> Presently, it recognizes the device but cannot find the network. As I said, I expect it will forget the device when I turn the computer off.

Do you mean that ndiswrapper does not keep the chosen configuration?
I'd say that you could connect the laptop through wire to the network and give wormser's suggestion a try.

---

### Post by ZOOstation on 2007-12-26
Usually, ndiswrapper keeps the info I give it but for some reason the button on my keyboard that activates the network card would be inactive and unable to be made active. And lshw would tell me the wireless network is UNCLAIMED.

But, I just started up the computer and wireless is running without problem. Maybe Murphy's Law will hold true and now that I've asked for help it'll stop giving me problems. Or maybe the moment I shrug my shoulders and say, "Nevermind, problem solved," it'll crap out again.

For now, I'll say case closed.

---

### Post by ZOOstation on 2007-12-27
Okay, the system detects the card just fine, and the card can find the network. But the internet still doesn't work. The network is not down. Suggestions?

---

### Post by xeth_delta on 2007-12-27
> **ZOOstation said:**
> Okay, the system detects the card just fine, and the card can find the network. But the internet still doesn't work. The network is not down. Suggestions?

Is the network encrypted? WEP, WPA1/2?

---

### Post by ZOOstation on 2007-12-28
Wep

---

### Post by xeth_delta on 2007-12-28
One thing I noticed, at least while using wicd instead of network manager, is that the pass phrase has to be written between quotes (i.e.: "passphrase"). Please try that and write back.

---

### Post by ZOOstation on 2007-12-29
Maybe it's because I use network manager, but if I use quotes it counts them as characters in the wepkey. Unless that's not the passphrase you're thinking of, but it's the only one my internet connection uses.

At present, connectivity is unusually spotty. All the other computers in the house, all on Windows, get a super fast connection and mine sometimes delays, sometimes dips out, wavers back and forth within minutes.

---

### Post by clayt0njknight on 2007-12-29
What I find ironic here is that the lspci output almost looks like it's using either restricted drivers or something from the bcm43xx fwcutter.  under module I would think it would say 'ndiswrapper' instead of the kernel version.  At least that's what I've always seen in using ndiswrapper.  IF it truly is using restricted drivers, or is using something linux-native and you're trying to use ndiswrapper you first need to blacklist the native drivers.

---

### Post by ZOOstation on 2007-12-29
I'm not presently using ndiswrapper because I'd been having such difficulty. And since I removed it, the computer has consistently recognized the network card and found the network with what it claims is a signal between 89% and 99%.

Would you suggest I give ndiswrapper another try?

---

### Post by clayt0njknight on 2007-12-30
It's worth a shot.  can't really hurt.  But I'd remove the drivers you are currently using before attempting to use ndiswrapper.  You could also go into the network manager at the top of the screen and try to force a manual connection (select wireless connection, choose network, dhcp, and set whatever security settings you use).

---

### Post by ZOOstation on 2007-12-30
I've blacklisted bcmxx, installed ndiswrapper, and loaded the wireless driver from my windows driver recovery dvd. And just like before, it needs coaxing to find the card:

```
sudo modprobe ndiswrapper
```

Then it remembers the network configuration and pulls it right up. Sometimes it isn't receiving a signal, but that's less important than...

When I restart the computer, it forgets where the card is again and I have to do "sudo modprobe ndiswrapper" again. I've read lots of different guides to this problem, and I've tried lots of different ways to make it load ndiswrapper at boot, and none of them have made a difference.

Suggestions? Do you need me to share any more info?

---

### Post by ZOOstation on 2007-12-31
I found a WifiDocs guide in the community support documentation that worked beautifully for me. Thanks to all for their help.

---

