---
title: "Okay, what's my wireless?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Shmook on 2008-02-02
I just acquired a new laptop and would love to set up the wireless adapter I know lives inside, but don't know how to find out WHAT the driver is so I can continue on the journey.

I'm guessing its somewhere in the output of lspci, which reads:

```

bx2:/home/brian# lspci
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:

```

All I see is a modem and 2 ethernet controllers. Any ideas?

Oh and ifconfig offers no acknowledges wireless device either. Thanks!

---

### Post by Paul820 on 2008-02-02
This would be it, Atheros are known to be tricky :(
> 02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by raptir on 2008-02-02
This one is your wireless adapter:

```
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

802.11 a/b/g is an architecture for wireless communication.

EDIT: Gah, beat me.

---

### Post by Presto123 on 2008-02-02
Have you checked to see if it shows up in Restricted Drivers Manager?

Also, in that output you can see on one of the ethernet controllers it has:

```
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

You see that 802.11abg? That should be the wireless. :)

*Edit*Bah, you all beat me.**

---

### Post by Shmook on 2008-02-02
Ha! Thanks, both

---

### Post by Whiffle on 2008-02-02
Its the madwifi drivers that should work with yours.

---

