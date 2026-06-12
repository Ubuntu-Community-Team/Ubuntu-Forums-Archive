---
title: "Check ethernet card"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by slink on 2007-10-11
Hi 

I need to check if my ethernet card is working properly, how can I do that?

Do I need to post more information?

---

### Post by dwhitney67 on 2007-10-11
First, try pinging another computer or the router within your local area network, or if you do not have such, try pinging an outside source (e.g. [www.google.com](www.google.com)).  The command, which needs to be run from a terminal, is:

[FONT="Courier New"]$ ping <IP address or URL>[/FONT]

where <IP address or URL> is replaced with the IP address or URL you are attempting to ping.

If that fails, then let's examine your hardware.  First determine the type of ethernet controller (NIC) that is present on your system:

[FONT="Courier New"]$ lspci | grep Network[/FONT]

Then post the results; maybe then I or someone else can help you.

---

### Post by netventure on 2007-10-11
You can also use mii-diag and mii-tool to get information on the status of the ethernet controller.

--NV

---

### Post by thewrinklyninja on 2007-10-11
theres also ipconfig or is it ipcfg from the terminal. I forget which

---

### Post by Joeb454 on 2007-10-11
I know it might sound really stupid or ignorant of me, but are you using the computer that you want to check the NIC of?

I.e. are you posting off the computer that the ethernet card is in, because surely that means it's working??

---

### Post by slink on 2007-10-11
> are you posting off the computer that the ethernet card is in ?

No. I am at another computer. 

This is what the un-connected computer yelds:

```
felix@ordinador:~$ lspci | grep Network
felix@ordinador:
```


nothing, so I did:

```
felix@ordinador:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)

```
and then:

```
felix@ordinador:~$ mii-diag 
Using the default interface 'eth0'.
SIOCGMIIPHY on eth0 failed: Operation not supported

felix@ordinador:~$ mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found
```

That does not look good...

---

### Post by slink on 2007-10-11
> You can also use mii-diag and mii-tool to get information on the status of the ethernet controller.

I sudoed it:

```
felix@ordinador:~$ sudo mii-diag 
Password:
Using the default interface 'eth0'.
Basic registers of MII PHY #1:  3000 7849 0000 8201 01e1 0000 0000 0000.
 Basic mode control register 0x3000: Auto-negotiation enabled.
 Basic mode status register 0x7849 ... 7849.
   Link status: not established.
   End of basic transceiver information.

felix@ordinador:~$ sudo mii-tool
eth0: no link
```

---

