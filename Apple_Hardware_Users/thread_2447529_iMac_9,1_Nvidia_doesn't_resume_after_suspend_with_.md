---
title: "iMac 9,1 Nvidia doesn't resume after suspend with 20.04"
date: 2020-07-20
forum: Apple Hardware Users
---

### Post by mixmastamyk on 2020-07-20
Hi,

I have an older 2009 iMac 9,1 with Nouveau (Nvidia) GFX on Ubuntu Mate 20.04.  It works quite well with one exception, it does not resume from sleep.  Doesn't wake up by touching the keyboard/mouse, or pressing the power button on the back.

I tried sleeping via the menu and the command `systemctl suspend`.  Didn't make a difference.

To recover we must hold down the power button for 5 seconds or so, which does a hard reset.

Specs below (upgraded to 8GB RAM):

[https://everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.66-20-inch-aluminum-early-2009-specs.html](https://everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.66-20-inch-aluminum-early-2009-specs.html)

At first I thought maybe it wasn't registering the power button, but I notice it *does* register it to bring up the shutdown dialog.  Didn't find much in this file, which is often mentioned:

```

> cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
EC        S3	*disabled  platform:PNP0C09:00
OHC1      S3	*enabled   pci:0000:00:04.0
EHC1      S3	*enabled   pci:0000:00:04.1
OHC2      S3	*enabled   pci:0000:00:06.0
EHC2      S3	*enabled   pci:0000:00:06.1
GIGE      S5	*disabled  pci:0000:00:0a.0

```

Does anyone know a fix for this, or what can I log to find out?

---

### Post by iociatos on 2020-09-03
Same problem with MacBookPro4,1 and  Ubuntu Budgie 20.04.1.
Also, the wifi does not connect in the 5 GHz band and the Bluetooth mouse cannot connect.

---

