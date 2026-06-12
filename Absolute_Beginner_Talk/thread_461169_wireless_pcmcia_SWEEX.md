---
title: "wireless pcmcia SWEEX"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by the_tavi on 2007-06-01
Hello all,

 Old within computers, very beginner with Linux (Feisty Fawn 7.04 first love :) ), I am facing a problem that I do not really understand. I have a Laptop IBM ThinkPad T40, improved with an internal original IBM wireless card. Supplementary I use one external PCMCIA Sweex card, that used to be more efficient than the internal (in Windows) when having not very strong wireless network (practically is more efficient pointed in  the direction of the wireless router).
  
 Now,  my Feisty recognize both of the cards, my network manager is working fine, but the signal of Sweex card is much more weak than in Windows, used in the same conditions. Actually, I cannot connect from the same spot using external card and LINUX instead of Windows. Maybe it is  a strange driver, or there is something missing.

 Can you please help me with a few ideas? I will post the result of "lspci" below:

Thank you,

Tavi

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
	Subsystem: Intel Corporation Unknown device 2712
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
	Subsystem: IBM Thinkpad R50e model 1634
	Flags: bus master, medium devsel, latency 66, IRQ 11
	Memory at c0201000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 8000 [size=64]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
	Subsystem: Atheros Communications, Inc. TP-Link TL-WN510G Wireless CardBus Adapter
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at c4000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

---

