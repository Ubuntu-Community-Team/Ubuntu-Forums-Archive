---
title: "Linksys WMP54G, Drivers not working"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by fromp on 2007-02-13
im pretty new to ubuntu,
i have a Linksys WMP54G wireless card.
iv installed ndiswrapper, configured it, used the Ralink driver and The rt2x00 Open Source Project driver with ndis
the ralink wont work, the card is still ra0 on iwconfig. and the rt2x00 wont compile/install (i dont really know how to work with tar.gz's)

any ideas? there are no other listed working drivers, it says the linksys one wont work with ndis

thanks,
fromp

---

### Post by ukripper on 2007-02-14
> **fromp said:**
> im pretty new to ubuntu,
i have a Linksys WMP54G wireless card.
iv installed ndiswrapper, configured it, used the Ralink driver and The rt2x00 Open Source Project driver with ndis
the ralink wont work, the card is still ra0 on iwconfig. and the rt2x00 wont compile/install (i dont really know how to work with tar.gz's)

any ideas? there are no other listed working drivers, it says the linksys one wont work with ndis

thanks,
fromp

run following and paste here

$ sudo lspci

$ sudo iwconfig 

and paste contents present in interfaces file by running :
$ sudo gedit /etc/network/interfaces

---

### Post by fromp on 2007-02-14
the lspci returns:
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory
Controller Hub] (rev 03)
0000:00:01.0 VGA compaatible controller: Intel Corporation 82810E DC-133 CGc [Chi
pset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
0000:01:0a.0 Network controller: RaLink: Unknown device 0301  *I think you want this one*
0000:01:0b.0 Communication controller: Contextant HCF 56k Data/Fax Modem (rev 08)

iwconfig returns:
lo	no wireless extensions.

ra0	RT61 Wireless  ESSID:""
	Mode:Auto  Channel:0
	RTS thr=0 B  Fragment thr=0 B
	Encryption key: off  (no space there, but it added a smiley so i out one in)
	Link Quality:0  Signal level:0  Noise level:113
	Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
	Tx excessive retries:0  Invalid misc:0  Missed beacon:0

sit0	no wireless extensions.

gedit is not a recognized command, but that file only has comments and a loopback thing for lo

---

