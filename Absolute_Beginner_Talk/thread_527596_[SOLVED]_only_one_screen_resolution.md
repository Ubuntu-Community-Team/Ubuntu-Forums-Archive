---
title: "[SOLVED] only one screen resolution"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by kchang on 2007-08-16
When I try to change the screen resolution via System>Preferences>Screen Resolution I am only allowed to select one resolution size 640x480. I know that Ubuntu automatically detects the best settings, but this is a little ridiculous.

I am running Ubuntu 7.04.

---

### Post by overdrank on 2007-08-16
> **kchang said:**
> When I try to change the screen resolution via System>Preferences>Screen Resolution I am only allowed to select one resolution size 640x480. I know that Ubuntu automatically detects the best settings, but this is a little ridiculous.

I am running Ubuntu 7.04.

HI maybe the thread will help
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck!

---

### Post by Jimmyfj on 2007-08-16
We would need som more information about your graphics card in order to help out. The make of the card.

---

### Post by MockY on 2007-08-16
If you have a gpu from Nvidia, check and see if you have any restricted drivers to enable. Go to System - Administration - Restricted drivers manager. Enable the appropriate drivers.

If there is none, try install drivers via [**Envy**](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by kchang on 2007-08-16
> **overdrank said:**
> HI maybe the thread will help
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck!

Tried following that but to no avail.

As for a graphics card this is what I get when I "lspci"

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
**00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)**
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```

Any ideas?

---

### Post by overdrank on 2007-08-16
> **kchang said:**
> Tried following that but to no avail.

As for a graphics card this is what I get when I "lspci"

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
**00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)**
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
```

Any ideas?
HI I hope this works it has helped others
[http://ubuntuforums.org/showthread.php?t=520250&highlight=Intel+Corporation+82845G&page=2](http://ubuntuforums.org/showthread.php?t=520250&highlight=Intel+Corporation+82845G&page=2)
Good luck!

---

### Post by phidia on 2007-08-16
In community docs there's a how-to for your card [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

---

### Post by overdrank on 2007-08-16
> **phidia said:**
> In community docs there's a how-to for your card [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

Even better!:)

---

### Post by kchang on 2007-08-20
> **phidia said:**
> In community docs there's a how-to for your card [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

That did it. Thanks!

---

