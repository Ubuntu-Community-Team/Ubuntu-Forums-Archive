---
title: "24 inch Intel iMac Dapper wireless not working"
date: 2007-05-07
forum: Apple Intel Users
---

### Post by felixdzerzhinsky on 2007-05-07
How do I get the wireless card to work on the 24 inch Intel iMac under Feisty?


(Solved) I ended up using ndiswrapper and the Windows XP drivers from the Windoze (gaming...no other use for Windoze). They worked right away unlike the OSX  Appleairport2 driver which did not.

So when you are in your XP partition use Search and look for BCMW5  Copy the BCMW5.inf and BCMW5.sys  (information and system) files to a usbstick or cd. Then boot back into ubuntu. And follow the 'destructions' at:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Thanks for those who tried to help.

---

### Post by ronocdh on 2007-05-07
> **felixdzerzhinsky said:**
> How do I get the wireless card to work on the 24 inch Intel iMac under Dapper?
Take a look at [this post]("http://ubuntuforums.org/showpost.php?p=2505546&postcount=3") by Greywhind. It depends on the specific wireless chipset you have (type **sudo update-pciids** then **lspci** to find out), but if it's a Broadcom, hopefully this will be of some help.

---

### Post by felixdzerzhinsky on 2007-05-08
lspci -v

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit  Ethernet Controller (rev 22)
        Subsystem: Marvell Technology Group Ltd. Marvell RDK-8053
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at 4a300000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 1000 [size=256]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting

03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
        Subsystem: Apple Computer Inc. Unknown device 0087
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at 4a200000 (64-bit, non-prefetchable) [size=16K]
        Memory at 4a000000 (64-bit, prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2
        Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [13c] Virtual Channel
        Capabilities: [15c] Power Budgeting


dmesg:

sky2 v1.5 addr 0x4a300000 irq 169 Yukon-EC (0xb6) rev 2
sky2 eth1: addr 00:16:cb:9c:f1:26

eth1394: eth0: IEEE-1394 IPv4 over 1394 Ethernet (fw-host0)

Initially I am connecting to an unsecured network.

---

### Post by ronocdh on 2007-05-08
So did the post help?

---

### Post by chillin on 2007-05-09
I had a heck of a time finding documentation on enabling wireless. Check your sys profiler from OS X, the airport card is actually a Broadcom Wireless card.

Here you go:
[size=+1][[color=brown]Using Broadcom Wireless in Ubuntu Dapper 6.06[/color]](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)[/size]

There's 2 choices there, don't get confused. I chose not to use ndiswrapper (nice project, but something about it it seems... unholy).  I used  the instructions starting with '1.3' on that page (well, not that page, the edgy page of the same instructions).

The same instructions for Edgy helped me get wireless working on a Dell D600. I know... not an intel iMac, but it uses the same family of wireless card.

Best of luck.

---

### Post by felixdzerzhinsky on 2007-05-19
AirPort Card Information:

  Wireless Card Type:	AirPort Extreme  (0x14E4, 0x87)
  Wireless Card Locale:	Worldwide
  Wireless Card Firmware Version:	Broadcom BCM43xx 1.0 (4.80.79.1)

Nothing seems to work. Not bcm43xx-cutter or ndiswrapper. Any new ideas I can try?

---

