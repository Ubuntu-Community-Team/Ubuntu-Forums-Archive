---
title: "Brand new to Ubuntu, my first day."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by BeCreative on 2008-02-06
And I've had nothing but problems. My wireless card is a Linksys WPC54GS and I'm having the damndest time getting it to work.

The PC recognises it's there but I can't find an option to search for wireless networks and when I try to manually connect, it won't do that either.

I've tried installing it about 800 different ways but I'm at a complete loss.

Could anyone write me a retarded guy's guide to installing it, with every step broken down the point a 5 year old could do it?

I really, really like ubuntu but I'm starting to think it's not worth the hassle.

Thanks in advance.

---

### Post by ugm6hr on 2008-02-06
As a start - perhaps point us to any "How-tos" you've already tried.

Also - we need specific information - post the output from:

```
lspci
lshw -C network
```

---

### Post by OffAxis on 2008-02-06
I don't know anything about your specific card, but here's an excellent place to start
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by emarkd on 2008-02-06
I know you asked for a step-by-step, but [this guide]("http://blog.eksfiles.net/2007/12/30/using-the-linksys-wpc54g-v2-and-wpa-with-ubuntu-gutsy/") looks quite good.  Have you tried this?  If so, what went wrong?  If not, do you have any more specific questions we could help you with to get you going in that direction?

---

### Post by BeCreative on 2008-02-06
[http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php](http://kosmaczewski.net/blogs/tech/archives/2006/02/how_to_install_1.php)

[http://antonym.org/node/89](http://antonym.org/node/89)

Those are the ones I tried.

---

### Post by Tannster on 2008-02-06
DO NOT give up buddy.  I spent 2 days this week getting my WMP54G working, and its very worth the time.  I found all the info I needed in just the How-To section.

When I get off work I'll dig around for some info on your specific card.

---

### Post by BeCreative on 2008-02-06
joy@joy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
joy@joy-laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.08.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

---

### Post by yaknowwat on 2008-02-06
The problem is company's don't want to spend a time developing for a Operating System that isn't the most used one, so you got people who donate what time they have to figure out how to make one that has full functionality.

There is NdisWrapper I think it is that would allow you to do it but yeah...

By the way are you using WPA encryption or WEP or no encryption on your wireless network.

I hear WPA does not work with the Ndiswrapper driver, WEP is said to though.


There isa guide for installing it here though
[http://ubuntuforums.org/showthread.php?t=190967](http://ubuntuforums.org/showthread.php?t=190967)

---

### Post by ugm6hr on 2008-02-06
> 03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

And that command is *lshw -C network* (i.e. Capital C)

You need to activate restricted drivers (or use ndiswrapper).

Just do a search of these forums for BCM4318 - there should be loads of similar threads in here.

Here are a selection:
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
[http://ubuntuforums.org/showthread.php?t=653946&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=653946&highlight=bcm4318)
[http://ubuntuforums.org/showthread.php?t=684846&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=684846&highlight=bcm4318)

---

### Post by twiceasworn on 2008-02-06
edit: nevermind

---

### Post by jaytek13 on 2008-02-06
> **twiceasworn said:**
> I am confused, above you say you are trying to get a linksys to work, yet your lspci shows you have a Broadcom in your machine....?

Many linksys products are sold with broadcom chipsets.

---

### Post by twiceasworn on 2008-02-06
yeah i realized that right after i posted :/.  Fortunately I was lucky and my wireless worked out of the box so I really havent delved into this stuff much.

---

