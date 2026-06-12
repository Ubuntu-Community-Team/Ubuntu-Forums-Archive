---
title: "Wifi on 6.10?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by MikeJ112 on 2007-05-22
Hi, have just installed Ubuntu 6.10 and so far so good, nice clean interface and really useful tools. I have installed on a Toshiba Equium L-20 laptop, which has an Atheros wifi adapter built in. During setup it asked me for my WEP key, but I can only seem to connect via cable. Have checked in Device Manager, and it is showing but the Device type is unknown. Is this a driver issue, or am I doing something wrong!

---

### Post by Kobalt on 2007-05-22
It may be a driver problem : do you know the exact model of your wifi card ? If not, please post the output of the following command line : ```
lspci
```

---

### Post by MikeJ112 on 2007-05-22
Also, wifi working fine on XP Home, im dualbooting

---

### Post by MikeJ112 on 2007-05-22
> **Kobalt said:**
> It may be a driver problem : do you know the exact model of your wifi card ? If not, please post the output of the following command line : ```
lspci
```

michael@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

---

### Post by MikeJ112 on 2007-05-22
Its the one right at the bottom :)

---

### Post by Kobalt on 2007-05-22
This [HowTo]("http://ubuntuforums.org/showthread.php?t=38972") should help you install your card drivers.

---

### Post by MikeJ112 on 2007-05-22
will work with onboard WLAN as well?

also, the http link is out of date :S

---

### Post by Kobalt on 2007-05-22
It is supposed to work with this kind of chipset yes... Suposedly you should get this card working installing the *linux-restricted-modules-2.6.20-15-generic* package (through Synaptic). But I must admit the drivers seem to be buggy for some...

---

### Post by MikeJ112 on 2007-05-22
Still not got this setup, bit of a disapointment really. Am getting a mid-range pc soon so might install Ubuntu primarily on there and just wire it up!

---

