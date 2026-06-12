---
title: "Wireless Woes"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by MrTrumpets on 2006-01-08
Hi all.

I can't get drivers to load right.  I loaded the 2 drivers from my CD-ROM (that I've used in the last version of Ubuntu) and now it's not working.  Here's what I get when I check my drivers.
```
$ ndiswrapper -l
Installed ndis drivers:
wmp11nds        driver present
wmp11nds.sys    invalid driver!

```

When I look at my hardware I get this.
```
$  lspci
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 554d
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 556d
0000:02:09.0 Ethernet controller: Linksys, A Division of Cisco Systems: Unknown device 2120

```

That Linksys at the bottom is my wireless card.  It's WMP11 v2.1.  If anyone has the proper driver, I'd LOVE it if you could send it to me, [email]mrtrumpets@gmail.com[/email] or help me find the right driver online.

I don't even think I have ndiswrapper installed right.  The messages on the screen sent me in a loop.  I can probably reproduce the messages if needed for copy-paste sessions.

btw.. I was following the suggestions STRAIGHT from the [wiki]("https://wiki.ubuntu.com/forum/hardware/ndiswrapper").

---

### Post by r_a_trip on 2006-01-08
A search in Google for ***Ethernet controller: Linksys, A Division of Cisco Systems: Unknown device 2120*** gave me this (third hit):

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/ListItoP](http://ndiswrapper.sourceforge.net/mediawiki/index.php/ListItoP)

On this page search in Firefox with [CTRL] - F for ***Ethernet controller: Linksys, A Division of Cisco Systems: Unknown device 2120***

You'll get to this section:

[I]# Card: PCMCIA card INPROCOMM IPN2120 distributed by truckstop.net

    * Chipset: INPROCOMM
    * pciid: 17fe:2120
    * Driver: ndis 1.1-4 w packaged WinXP driver and kernel 2.6.11 on Debian unstable
    * Other: Truckstop.net is currently in litigation so the cards can be had for $10. The driver can be had from [http://www.truckstop.net/support/C130-Driver.zip](http://www.truckstop.net/support/C130-Driver.zip). lspci reports: Ethernet controller: Linksys, A Division of Cisco Systems: Unknown device 2120. I originally spotted this one on a support list for ndis under the Linksys brand. [/I]

I don't know if the driver is any good, my wireless PCMCIA card is from SMC with ADMtek 8211 chip so I can't try it out, but it's worth a try. 

Don't wait too long though, as the post says that Truckstop is in litigation. It's anyones guess how long this stuff stays online.

---

### Post by MrTrumpets on 2006-01-08
Awesome.. Thanks for the info.  I did find out that I was using the wrong inf and sys files.  Or at least I think I was.. Now I get this.
```
$ ndiswrapper -l
Installed ndis drivers:
lsipnds driver present, hardware present
lsipnds.sys     invalid driver!
```

That's an improvement!

I also found the correct drivers indicated on the "list" of known drivers from the wiki.


Any other suggestions would be great.

---

