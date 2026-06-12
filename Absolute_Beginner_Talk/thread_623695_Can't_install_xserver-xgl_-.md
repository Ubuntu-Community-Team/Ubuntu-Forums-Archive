---
title: "Can't install xserver-xgl -"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by redtag on 2007-11-26
I'm trying to get visual effects working...but I can't install xserver-xgl

Using Synaptic Package Manager, I search for "xserver-xgl" and when it shows up, I mark for installation and then I get this error:

xserver-xgl:
 Depends: libglitz-glx1  but it is not installable
 Depends: libglitz1 (>=0.4.3+cvs20050728) but it is not installable


any ideas on what's going on and how to fix it?

---

### Post by ukripper on 2007-11-26
what graphics card you have?

---

### Post by redtag on 2007-11-26
I think it's Mobile Intel GrahpicsMedia Accelerator X3100

that's what it says on my laptop.
Is this the graphics card?  if not, how can I find out?

Thanks!

---

### Post by ukripper on 2007-11-26
> **redtag said:**
> I think it's Mobile Intel GrahpicsMedia Accelerator X3100

that's what it says on my laptop.
Is this the graphics card?  if not, how can I find out?

Thanks!

Do following command and look for you graphics card entry:

```
lspci
```

---

### Post by redtag on 2007-11-26
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)


this it?

just incase, here's everything that came up:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

---

### Post by OldGrey on 2007-11-26
When I first upgraded to Gusty from Fiesty I had trouble with the effects. Xserver-xgl fixed them, but it has its own problems see: [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/155284](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/155284).
Eventually I did a clean install and that sorted the effects issue out without recourse to xserver-xgl.

---

### Post by redtag on 2007-11-26
I just bought this new computer about a month ago.  It had vista on it.  I was getting sick of it and I decided to install ubuntu 7.10.  First time using a linux software.  I just installed it tonight, and I am trying to get it set up so it looks cool and works good.

I'm have a couple of problems, one of which being the xserver-xgl, the other is the wifi isn't working.

---

### Post by ukripper on 2007-11-26
Have you enabled restricted drivers module?
ok try this :

Enable all your sources first !
System>>Admin>>Software Sources tick all of them under ubuntu software tab.

---

### Post by Xavieran on 2007-11-26
What kind of wireless card do you have?

is it this one :
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

Or this one:
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

---

### Post by Ub1476 on 2007-11-26
> **redtag said:**
> I think it's Mobile Intel GrahpicsMedia Accelerator X3100

that's what it says on my laptop.
Is this the graphics card?  if not, how can I find out?

Thanks!

This graphic card doesn't require XGL to run desktop effects. However, I think your graphic card is blacklisted.

Try to run compiz in the terminal, if you get a warning saying someting like "no whitelisted driver found", follow this [thread]("http://ubuntuforums.org/showthread.php?t=582112").

```
compiz
```

Also make sure that you are using the* Intel 945* driver. Check by going into System>Administration>Screens and graphics>Graphics card>Driver:

---

### Post by redtag on 2007-11-26
I got xserver-xgl working!
and compiz!


My wireless still isn't working.  
My wireless is:
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Is there something I need to download?

---

### Post by ukripper on 2007-11-27
> **redtag said:**
> 


My wireless still isn't working.  
My wireless is:
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

Is there something I need to download?

follow this guide [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

