---
title: "Video card"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by lilyoshi13 on 2007-06-01
How can if figure out what video card i have.  I have a dell optiplex GX240

---

### Post by taurus on 2007-06-01
Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by lilyoshi13 on 2007-06-01
I got

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)


Now what is my video card

---

### Post by taurus on 2007-06-01
> **lilyoshi13 said:**
> I got

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
**[COLOR="Blue"]01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF[/COLOR]**
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

Now what is my video card

There you go.

---

### Post by lilyoshi13 on 2007-06-01
ps can i run battlefield 2 on this video card

---

### Post by strider_mt2k on 2007-08-24
The card is very limited in it's capabilities unfortunately, but the GX240 comes from a line of machines primarily intended for business use and not the cool stuff we're doing with them. ;)

---

### Post by jazz1 on 2007-10-19
I called Dell and asked what they would recommend for an upgrade on an old GX240 and they suggested an XTASYRadeon X13000 256 MB AGP card. Cost is $109.00. Does anyone think this is worth spending money on?

My needs are modest but the Rage Pro 128 LT really has trouble when I move windows. I'm on the edge of simply cutting my loses (well I got it for $75.00 with CRT monitor) and just by a Dell configured Ubuntu desktop. I'd like to add a 19 or 20 in LCD as the CRT is killing my eyes. So maybe a whole new system is the way to go? Again my needs are modest.

---

