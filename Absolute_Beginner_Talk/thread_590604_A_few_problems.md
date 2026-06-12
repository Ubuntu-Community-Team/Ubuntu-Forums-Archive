---
title: "A few problems"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by taco89 on 2007-10-24
Alright, I decided to  completely wipe my hard drive and just install Ubuntu 7.10. However, I got a couple errors/notices.

I got this one near the end of installation:
```

_Cannot access security updates_

The security updates on security.ubuntu.com couldn't be
accessed, so those updates will not be made available to
you at this time. You should investigate this later.

Commented out entries for security.ubuntu.com have been
added to the /etc/apt/sources.list file.

```

I suspect this has to do with another problem I'll list soon.

I got this message when I tried to activate the "Firmware for Broadcom 43xx chipset family":
```

The software source for the package
     bcm43xx-fwcutter
is not enabled

```

And possibly the error I'm most frustrated with... I can't connect to the internet. I have a wireless Linksys router and Ubuntu won't read the signal for some reason and won't let me connect (won't even list the connections).

So can I get some help please?


[EDIT]

If it helps, here is what I get when I do the 'lspci' thing:
```

00:00.0 Host bridge: ATI Technical Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technical Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technical Inc 437A Serial ATA controller (rev 80)
00:12.0 IDE interface: ATI Technical Inc 4379 Serial ATA controller (rev 80)
00:13.0 USB Controller: ATI Technical Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technical Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technical Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technical Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technical Inc standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technical Inc SB450 HD Audio (rev 01)
00:14.3 ISA bridge: ATI Technical Inc SB400 PCI-ISA Bridge (rev 80)
00:14.4 ISA bridge: ATI Technical Inc PCI-PCI Bridge (rev 80)
01:05.0 SGA compatible controller: ATI Technical Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Network controller: Broadcom Corporation BCM4306 802, 11b/g wireless LAN Controller (rev 02)

```

---

### Post by oldos2er on 2007-10-25
Open your sources.list (gksudo gedit /etc/apt/sources.list), and uncomment the repositories you need.

---

### Post by mmmfottrell on 2007-10-25
I honestly had the same problem with the b43cmxx cutter thingy.

Connect to the internet via direct ethernet cable.

Restart your computer.

Go to System >> Administration >> Restricted Drivers Manager

You should be able to download the required drivers now. 

Restart and everything should work fine.

---

