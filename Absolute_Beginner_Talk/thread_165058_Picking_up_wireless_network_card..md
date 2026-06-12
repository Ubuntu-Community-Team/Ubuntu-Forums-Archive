---
title: "Picking up wireless network card."
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by jpapciak on 2006-04-23
Hello, if this has been answered already on the forums, I appologize, I have searched for an answer quite a bit.  I am very new to the whole Linux scene but do know my way around Windows decently.  I installed Ubuntu, and read up on how to use it wirelessly, and was using it on my laptop (wireless card built in).  Well, my card went dead, and instead of getting it fixed, I had a Linksys card laying around in an attempt to put wireless internet on my grandpa's old laptop.  I just popped that in to a slot on the side of my laptop, but Ubuntu is not picking that up.  Any suggestions?

---

### Post by verbalshadow on 2006-04-23
can you post the output of
```
lspci
```

do the power and link light turn on?

---

### Post by Nikusan on 2006-04-23
[QUOTE=jpapciak]Hello, if this has been answered already on the forums, I appologize, I have searched for an answer quite a bit.  I am very new to the whole Linux scene but do know my way around Windows decently.  I installed Ubuntu, and read up on how to use it wirelessly, and was using it on my laptop (wireless card built in).  Well, my card went dead, and instead of getting it fixed, I had a Linksys card laying around in an attempt to put wireless internet on my grandpa's old laptop.  I just popped that in to a slot on the side of my laptop, but Ubuntu is not picking that up.  Any suggestions?[/QUOTE]

Are you familiar with the [Ndiswrapper page]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") on the Ubuntu Wiki?

---

### Post by jpapciak on 2006-04-24
[QUOTE=verbalshadow]can you post the output of
```
lspci
```

do the power and link light turn on?[/QUOTE]

Here is my output from lspci

```

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cbb2 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Cont roller Audio Device (rev 02)
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two -Port PHY/Link-Layer Controller
0000:00:0a.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-L ayer Cont. an
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.1 1b MAC (rev 20)

```

The power light is turned on, but the light that says "link" next to it is not on.  I'm going to try the Ndiswrapper thing now.

---

