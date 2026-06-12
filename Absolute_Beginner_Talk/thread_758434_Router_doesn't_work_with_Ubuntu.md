---
title: "Router doesn't work with Ubuntu"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by The Cheesiest on 2008-04-18
Hey guys, I'm very new to Ubuntu, and so far I'm loving it.  But there is one problem, I'm dual-booting Windows XP Media Center Edition with Ubuntu 7.10, and in Ubuntu, my router doesn't turn on plus there is no options for wireless in the Network settings.  I've tried all the basic stuff and the stuff in the help articles.  Please I would really like some advice, if you would like results from certain terminal commands, or router info I'll provide it.  Thank you very much. 

~The Cheesiest

P.S. Sorry for the bad English.

---

### Post by joshrobinson on 2008-04-18
you mean the wireless card in your pc correct? not the router?
could you post the output of
```
lspci
```

---

### Post by The Cheesiest on 2008-04-18
Yes sir. :)

And thanks for the reply.

---

### Post by The Cheesiest on 2008-04-18
Nothing comes up when I run the command. :confused:

Sorry, I'm very novice. Any help would be greatly appreciated. ](*,)

EDIT: Never mind.  Here is the info:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:03.0 PCI bridge: PLX Technology, Inc. PEX 8111 PCI Express-to-PCI Bridge (rev 21)
01:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
02:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
02:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)

Thanks again. :)

---

