---
title: "Quick NIC question"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by feistyfirsttimer on 2007-08-01
I'm a complete n00b when it comes to networking.  I don't even know what a NIC *looks* like.

Anyway - my computer's previous owner had it on a network.  And I'm thinking of making a little home network.  I want to know if my computer still has a NIC.  So, how do I find out whether it still contains one?  Other than opening the computer up and looking inside (which wouldn't do me much good anyway - as I already said, I don't know what a NIC looks like).

---

### Post by w4ett on 2007-08-01
From the terminal type:

```
lspci
```

and post the results back here and let us have a look-see :)

---

### Post by feistyfirsttimer on 2007-08-01
OK...

martin@x-box:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
martin@x-box:~$ 

Is there a NIC there?

---

### Post by w4ett on 2007-08-01
Right here:
> 
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

Physically you will be looking for what appears to be a large telephone socket, either on the I/O backplate or in one of the PCI expansion bus card slots

It will be there.

---

### Post by feistyfirsttimer on 2007-08-01
Thanks w4ett!!

---

### Post by w4ett on 2007-08-01
No problem...good luck

---

