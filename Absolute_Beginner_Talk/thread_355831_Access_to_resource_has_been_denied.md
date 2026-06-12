---
title: "Access to resource has been denied"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-02-07
I originally posted a thread about how to install a scanner driver here:[http://www.ubuntuforums.org/showthread.php?t=353303]("http://www.ubuntuforums.org/showthread.php?t=353303")

It's an HP Scanjet 4370. That was never resolved, but then I found a deb file here: [http://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&re lease_id=453913]("http://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&re lease_id=453913") and installed it.
But now when I try to access XSane I get: 
Failed to open device 'HP3900:libusb:004:002':
Access to resource has been denied

---

### Post by shareMenaPeace on 2007-02-08
Hi, 
are you sure the scanner is set on the right slot?

```
lspci 
```

to check the slot - post here the output.

gl

---

### Post by kliljedahl on 2007-02-08
I'm at work now. I'll do it this evening when I get home.

---

### Post by kliljedahl on 2007-02-08
> **shareMenaPeace said:**
> Hi, 
are you sure the scanner is set on the right slot?

```
lspci 
```

to check the slot - post here the output.

gl

I'm home now, here's what I got: 
lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 USB Controller: NEC Corporation USB (rev 43)
01:09.1 USB Controller: NEC Corporation USB (rev 43)
01:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by kliljedahl on 2007-02-10
> **kliljedahl said:**
> I'm home now, here's what I got: 
lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 USB Controller: NEC Corporation USB (rev 43)
01:09.1 USB Controller: NEC Corporation USB (rev 43)
01:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Still nothing

---

