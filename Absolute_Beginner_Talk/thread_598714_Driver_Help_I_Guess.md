---
title: "Driver Help I Guess?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jatoskep on 2007-10-31
I recently got Ubuntu and have been loving it, but for some reason it seems to run a lot slower than when I had windows on this machine. Youtube and flash games lag like hell, firefox freezes a lot, and it's just sort of laggy in general. Would this have to do with drivers? Thanks in advance! ^_^

---

### Post by Regel on 2007-10-31
What's your hardware like?

I think the problem might be your graphic card's driver. "Vesa"-driver is extrimely slow.

---

### Post by taurus on 2007-10-31
Can you post the spec of your machine?  Have you installed any restricted driver for your graphic card?

I assume you installed Gutsy, 7.10.

---

### Post by jatoskep on 2007-10-31
It's a crappy old Dell Dimension 3000. It's got integrated video, 512MB RAM, a Celeron. Not completely sure all the specs.
And things like this ran just fine before I put Ubuntu on, so it isn't that the machine can't handle it.

---

### Post by jatoskep on 2007-10-31
> **taurus said:**
> Can you post the spec of your machine?  Have you installed any restricted driver for your graphic card?

I assume you installed Gutsy, 7.10.

Yes, it is Gutsy, and I haven't messed with the drivers at all yet.

---

### Post by taurus on 2007-10-31
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by jatoskep on 2007-10-31
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by jatoskep on 2007-10-31
Bump. :3

---

