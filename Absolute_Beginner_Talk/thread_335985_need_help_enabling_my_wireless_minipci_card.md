---
title: "need help enabling my wireless minipci card"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by chrido64 on 2007-01-11
Hi everyone,

I just installed Ubuntu on a Dell XPS notebook (first generation). I only tried the live cd before, so I am a real beginner at linux.
everything seems to be running fine except the wireless card
my wireless card is a dell truemobile 1350. 
Under Windows XP there is a key combination to "turn on" the wireless receiver : Fn+F2, but it seems to have no effect with Ubuntu.
i found another post with similar problem but the explanations are a little to difficult for me;

[http://www.ubuntuforums.org/showthread.php?t=295113&highlight=enabling+wireless+interface](http://www.ubuntuforums.org/showthread.php?t=295113&highlight=enabling+wireless+interface)

Since the card in that post is different from mine i'm not sure what exactly to do if i try the same approach. I did check in the synaptic package manager that the restricted modules are installed, but after that I am a little lost

if i type dmesg i get (i'm only copying and pasting what seems relevant to my pb)

```
[17179856.456000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179938.800000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179950.384000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179950.396000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180124.872000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180291.640000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180291.652000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17180565.340000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[17180565.340000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
```


is the keycode e008 in relation to FnF2?
if yes how do i program it to activate the wireless receiver?


when i type in terminal : iwconfig, i get this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

for lshw i get this among other things:

 ```
 *-network:1 DISABLED
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                logical name: eth1
                version: 03
                serial: 00:90:96:a7:02:ff
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-27-386 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:fafec000-fafedfff irq:177
```

finally if it helps, lspci gives me this:

```
0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)0000:00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

---

### Post by Atomic Dog on 2007-01-11
[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306)

This should help.

---

### Post by chrido64 on 2007-01-12
Thanks a lot for your help
That fixed some of my problems

---

