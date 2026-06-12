---
title: "PCMCIA Woes"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Esqulax on 2007-06-29
How can i tell if my PCMCIA socket is being read?

I put in me wireless card, both the lights come on (and stay on), but theres no mention of it in lspci.
The output is:
> 
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1


If its not seeing the PCMCIA card.. is there a magic command to allow it to see it?

---

### Post by Esqulax on 2007-06-29
Mini update...
I read that i need to install pcmcia-cs... BUT (using sudo apt-cache search pcmcia) all i can find is:
linux-wlan-ng
and 
pcmciautils

is utils the same thing?

---

### Post by Esqulax on 2007-06-29
Ok... another go...

i tried 
pccarfctl ls

and i got:
Socket 0 Bridge:    [yenta_cardbus]    (bus ID:0000:00:0a.0)
Socket 0 Device:   [-- no driver--]        (bus ID:0.0)

The bottom one only appears when i put the card in.

ndiswrspper -l
bel6020: driver installed

Any ideas?

---

### Post by Esqulax on 2007-06-29
Ok.. im officially lost... i've been trying this for like 2 days! I've serached forums, websites and tried loads of crazy apts, and still at the same stage as above

Any help on this (other than a biiiig hammer) would be freakin awesome

---

