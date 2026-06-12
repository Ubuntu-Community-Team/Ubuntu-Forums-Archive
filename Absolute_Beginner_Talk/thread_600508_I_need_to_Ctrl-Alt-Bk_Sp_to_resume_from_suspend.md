---
title: "I need to Ctrl-Alt-Bk Sp to resume from suspend"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-11-02
Hi everyone,

Well the title almost says it all.  Anyone experienced this and what can be done about it if anything?

Thnx for reading.

---

### Post by Pumalite on 2007-11-02
Is your /swap=RAM?

---

### Post by xyz on 2007-11-02
> **Pumalite said:**
> Is your /swap=RAM?

Thanks for answering.
Your command line returns No such file or directory.

---

### Post by xyz on 2007-11-03
Now only this works:
[URL="http://ubuntuforums.org/showthread.php?t=315404&highlight=force+shutdown"] HOW-TO reboot only if all else fails
[/URL]

---

### Post by justsomedude on 2007-11-03
Do you by any chance have an Nvidia card?

I had the same problem, this wiki article helped me to fix it:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by xyz on 2007-11-04
Thanks for the reply.

> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)


---

